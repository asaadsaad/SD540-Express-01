### SD540-Express-01

Create an Express application that for a newsletter subscriptions. Given the following Schema:
```typescript
const NewsletterSchema = new Schema({
    interval: { type: String, enum: ['daily', 'weekly', 'monthly'], required: true },
    user: {
        _id: { type: Schema.Types.ObjectId, required: true },
        email: { type: String, required: true },
        fullname: { type: String, required: true }
    },
    subscription_status: { type: Boolean, default: true }
}, { timestamps: true });
```
The application accepts the following requests:
* `POST /newsletters` will receive an object with an `interval` value + `user` object from the request body, and save the user in the DB.
* Create a middleware and apply it to the previous `POST` route, use the [Class Validator](https://www.npmjs.com/package/class-validator) package, and check if the request body has valid properties and types. (Generate `tsconfig.json` file using the following command `npx tsc --init` and set `{ experimentalDecorators: true }`)
* `GET /newsletters?projection=emails` will return all user emails, for active subscriptions, in pages.
* `GET /newsletters/:user_id` will return the newsletter document for the specified `user_id`.
* `PUT /newsletters/:user_id` will update the user interval to another value received from the request body.
* `DELETE /newsletters/:user_id` will set the user subscription status to `false`.

