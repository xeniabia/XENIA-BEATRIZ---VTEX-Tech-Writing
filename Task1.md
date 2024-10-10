# How to create an order invoice integration

The order invoice notification is an important step in the flow of orders between sellers and marketplaces. When integrating orders fulfilled by VTEX sellers, it is necessary to include tracking codes and invoice data.

### To create integration, follow the steps below:

>Note:
The NotifyInvoice resource is required to use these API requests. It is included in the following roles OMS - Full access and IntegrationProfile - Fulfillment Oms, among other roles available in Admin. If you want to learn more about, access [Roles](https://help.vtex.com/en/tutorial/perfis-de-acesso--7HKK5Uau2H6wxE1rH5oRbc?utm_term=&utm_campaign=BRA_pmax_2023&utm_source=adwords&utm_medium=ppc&hsa_acc=9663921675&hsa_cam=20809358286&hsa_grp=&hsa_ad=&hsa_src=x&hsa_tgt=&hsa_kw=&hsa_mt=&hsa_net=adwords&hsa_ver=3&gad_source=1&gclid=Cj0KCQjw05i4BhDiARIsAB_2wfCBv6Vgl-wDAAsCXVzzKgCUDlYdgXg8otZbhMrfSzWdUTdRrtfN3GwaAjzCEALw_wcB).

#### 1. Send invoice information

For this step, use [Order invoice notification API](https://developers.vtex.com/docs/api-reference/orders-api#post-/api/oms/pvt/orders/-orderId-/invoice) (POST).

This method is used to enter invoice information for the order.

If you choose to invoice referencing the items, this process must be done at this stage.

The sum of the invoice values must be equal to the total order value, including shipping, for the total order to be considered invoiced.

Invoices can be verified in [Get order API](https://developers.vtex.com/docs/api-reference/orders-api#get-/api/oms/pvt/orders/-orderId-).

* “``invoiceNumber``” is the order invoice number.

* “``invoiceValue``” is the order invoice value.

* “``invoiceKey``” is the access code.

* “``invoiceUrl``” is the invoice URL.

* “embededInvoice” is the field where the XML of the order invoice must be inserted and is mandatory for the order status to be updated on certified integration marketplaces.
    

>Only one invoice notification should be sent per order.
Sending more than one notification for the same invoice can result in lost information.
Since this is a POST method, only the last notification is recorded.
To add missing information after the invoice notification, use [Update order's partial invoice API](https://developers.vtex.com/docs/api-reference/orders-api#patch-/api/oms/pvt/orders/-orderId-/invoice/-invoiceNumber-).
    

Base URL:

    https://{accountName}.{environment}.com.br/api/oms/pvt/orders/{orderId}/invoice

Body Example:
	
    {
    "type":"Output",
        "issuanceDate":"2024-01-31",
    "invoiceNumber":"9999",
    "invoiceValue":"10000",
    "invoiceKey": null,
    "invoiceUrl": null,
    "courier": null,
    "trackingNumber": null,
    "trackingUrl": null,
    "items": [
    {
        "id": "123",
        "price": 10000,
        "quantity": 1
        }
    ]
    }
    
#### 2. Send code and other tracking information on the invoice

For this step, use [Update order's partial invoice (send tracking number) API](https://developers.vtex.com/docs/api-reference/orders-api#patch-/api/oms/pvt/orders/-orderId-/invoice/-invoiceNumber-) (PATCH).

This is the method that should be used by the carrier to enter tracking and delivery information.

This step is necessary when the order invoice information is sent without tracking information, so the tracking information needs to be updated later.

As this is a PATCH method, only the billing tracking parameters will be filled in, which were left blank in the request in the previous step.

This data must be sent only once per invoice per order, unless it is necessary to change the tracking information sent.

It is necessary to send a tracking number.

* “``trackingNumber``” is the tracking code;

* “``trackingUrl``” must be filled in with a tracking URL;

* “``dispatchedDate``” is a shipping data;

* “``courier``” is the field dedicated to the carrier name.


Base URL:

    https://{accountName}.{environment}.com.br/api/oms/pvt/orders/{orderId}/invoice/{invoiceNumber}

Body example:

    {
      "trackingNumber": "87658",
      "trackingUrl": null,
      "courier": null
    }

#### 3. Send the tracking information

For this step, use [Update order tracking status API](https://developers.vtex.com/docs/api-reference/orders-api#put-/api/oms/pvt/orders/-orderId-/invoice/-invoiceNumber-/tracking) (PUT).

This method should be used by the carrier to insert tracking updates.

Unlike the previous steps, it is expected that multiple requests will be sent to this API. Since this is a PUT method, each new update will be inserted into the order information, through the ``courierStatus`` field.

All updates sent are recorded.

* “``isDelivered``” is the field that informs whether or not the order was delivered.

* “``deliveredDate``” is delivery data.

* “``events``” is the array that contains the location, data and description of the updates.

Base URL:

    https://{accountName}.{environment}.com.br/api/oms/pvt/orders/{orderId}/invoice/{invoiceNumber}/tracking
    
Body Example:

    {
    "isDelivered": false,
    "events": [
        {
        "city": "Rio de Janeiro",
        "state": "RJ",
        "description": "Coletado pela transportadora",
        "date": "2024-06-23"
        },
        {
        "city": "Sao Paulo",
        "state": "SP",
        "description": "A caminho de Curitiba",
        "date": "2024-06-24"
        }
    ]
    }
    
* Updates are sent continuously until the package is delivered to the recipient and this is reported when the `isDelivered` field is true.

![isdelivered](https://i.ibb.co/mTc4d9G/Captura-de-tela-2024-10-09-090849.png)
