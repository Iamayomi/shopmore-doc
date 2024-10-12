# API REFERENCES

```bash
Authorization: Bearer <YOUR_API_KEY>
```

**Endpoints**

* User

<table><thead><tr><th width="410"></th><th></th></tr></thead><tbody><tr><td>POST api/v1/auth/register</td><td>create new user</td></tr><tr><td>POST api/v1/auth/signin</td><td>user login in</td></tr><tr><td>POST api/v1/auth/{ID}/verify-email</td><td>user verify email</td></tr><tr><td>POST api/v1/auth/reset-password</td><td>user reset password</td></tr><tr><td>POST api/v1/auth/verify-password-reset-code</td><td>user verify password reset</td></tr><tr><td>POST api/v1/auth/{ID}/verify-phone</td><td>user verify phone</td></tr><tr><td>PATCH api/v1/auth/reset-password</td><td>user reset password </td></tr><tr><td>POST api/v1/auth/forget-password</td><td>user forget password</td></tr></tbody></table>



