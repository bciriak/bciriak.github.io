**Useful Videos:**
- Video1 - https://www.youtube.com/watch?v=dDpZfOQBMaU
- Video2 - https://www.youtube.com/watch?v=Yc2MJYwLqzs
- Video3 - https://www.youtube.com/watch?v=cRXSEPBK-G8
- Video4 - https://www.youtube.com/watch?v=VLk45JBe8L8
- Video5 - https://www.youtube.com/watch?v=wY8cRJJU6RQ
- Video6 - https://www.youtube.com/watch?v=TSW0Ybxs_bE

### Notes

#### Video1

- App Router
- using form action (server action)
- `const [state, formAction] = useFormState(createTodo,initialState)`
- `<form action={formAction}>...`
- server action
	- takes prevState, formData
	- zod validation schema + schema.parse
	- try insert into table `revalidatePath('/')`
	- return state
	- catch error return state with error
- progressive enhancement (JS disabled no matter)
- `const {pending} = useFormStatus()`
- deleting a todo is done also with `<form action={formAction}>`
	- hidden input with `value={id}` todo ID

#### Video2

- problems with only server actions by default
	- no client side validation
	- slow internet means long time to wait for response back with server validations
	- no validation of input and output from server action
- reactHookForm for the client side validations
	- no progressive enhancement
- validations on the server actions (zsa, safe-server-action)


## Creating a form

#### Server action only

##### Form Page
- needs to be client component `use client`
- `const [state, formAction] = useActionState(createTodo, initialState)`
- initial state => `ActionState`
- returning `Success` message and `errors` array
- no need for JavaScript enabled
##### Server Action
- must have `use server` at the top of the file
- must be async function
- validation with `zod`
- using `FormData`

#### React Hook Form with Zod and Server Action

##### Form Page
- needs to be a client component `use client`
- `useForm` from react hook form
- zod and zodResolver (resolver installed separately)
- 