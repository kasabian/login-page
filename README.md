### Minimal html markup for login page.

```html
<form onsubmit="alert('submit'); return false;">
    <label>
      Name:
      <input type="text" name="name">
    </label>
   
    <br />
    
    <label>
      Pass:
      <input type="password" name="pass">
    </label>
    
    <br />
    
    <button type='submit'>Submit</button>
  </form>
 ```
 ##### Summary 
 
 1. For disable browser autocomplete use autocomplete = off attribute.
 2. We use form tag for simplify handling some behavior. Like when user  press enter on any field and we can catch onsubmit event.
 
 ### For communication with backend
 
1. Plain XMLHttpRequest object or fetch api. Fetch api newest way for working with http transfer. And work with promise and can canceling request.

##### About body data type 

Set to hedear Content-Type for say which data type you send.

1. application/x-www-form-urlencoded 

```js
const data = 'name=' + encodeURIComponent(name) +
  '&surname=' + encodeURIComponent(pass);
```

Every component encode to utf8 format.

2. multipart/form-data

```js
  Content-Type: multipart/form-data; boundary=RaNdOmDeLiMiTeR

	--RaNdOmDeLiMiTeR
	Content-Disposition: form-data; name="name"

	Victor
	--RaNdOmDeLiMiTeR
	Content-Disposition: form-data; name="surname"

	Co
	--RaNdOmDeLiMiTeR--

```

Boundary is divider for data block. multipart/form-data usually using for send big data.

### Tokens and session

For understand what is token and why jwt token see video.

https://www.youtube.com/watch?v=vQldMjSJ6-w

1. Save token to local storage and use intrceptors for adding it to each request (use cookie bad idea for multi service architecture and CORS).
2. For updating accesToken use expirationTime don't use 401 status. Some situation you can update token in iterseptor also you can use js setInterval for check token expiration. 


### Work with permissions

For fetch permission info before you site loaded use angular2 'APP_INITIALIZER' DI Token. 

### Tab communications

Use localStorage for save login status and subscribe to localStorage change event for catch status on all open tabs.

##### Count how lot of tabs are open 

1. Each tabs create uniq kay in localStorage and update every few second own time. 
2. Use one kay for all tabs but need master tab for determine queue for tabs update.

And remove tabs which are not update long time.
