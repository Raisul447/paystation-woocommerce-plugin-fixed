![pay station logo](https://paystation.com.bd/images/logo/logo.png)

# PayStation WooCommerce Plugin – Bug Fixes


I have faced two major issues in the officially released PayStation WordPress plugin, and I’ve fixed them successfully.

---

## 🔍 1st Problem:
When a customer made a successful payment, WooCommerce was showing the order status as **Completed**, which should actually be **Processing** for most standard orders.

## 🔍 2nd Problem:

When a customer click on **Place Order** and then payment gateway opens, if the customer then clicks the browser’s back button and tries to place the order again, it shows an error **Payment failed: Duplicate invoice number.** Even if the customer adds another product and tries again, the same error is shown.


## 🛠️ Fix:
**You can simply download as ZIP file and replace your current plugin those issues will be resolved.** (You can also apply the fixes manually by editing the code.)

---

**1st issue**

File: `paystation-process.php`  
Line: 58

- Before:
`$order->update_status('completed');`

- After:
`$order->update_status('processing');`

---

**2nd issue**

File: `paystation-gateway.php`  
Line: 141

- Before:
`$invoice_number = 'WP' . $this->merchant_id . '-' . $order_id;`

- After:
`After: $invoice_number = 'WP' . $this->merchant_id . '-' . time() . '-' . $order_id;`
