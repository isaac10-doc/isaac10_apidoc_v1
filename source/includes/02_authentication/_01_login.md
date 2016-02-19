## Login

<aside class="notice">
There is no equivalent function for authenticating you as merchant.
</aside>

```http
POST /api/v1/authenticate HTTP/1.1

{
  "email": "you@example.com",
  "password": "customer password"
}
```

```javascript
isaac10.login('email', 'password');
```

> Response

```json
{
  "success": {
    "customer_number": "100001",
    "customer_token":  "abc123"
  }
}
```

### Params

<table>
  <tr>
    <th>Parameter</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><strong>email</strong></td>
    <td>
      Mail of the customer
      <ul>
        <li> required </li>
      </ul>  
    </td>
   </tr>
   <tr>
     <td><strong>password</strong></td>
     <td>
       Password of the customer
       <ul>
         <li> required </li>
       </ul>  
     </td>
    </tr>
  </table>

If `email` and `password` are not matching, error 404 will be returned.


If you wish to outsource the authentication entirely with _isaac10_, you can request customer number and API token, asked for the authorize header or JavaScript function `.authenticateCustomer` by this API call.

After the request, `.authenticateCustomer` together with transferred customer number and customer token will be called automatically.
