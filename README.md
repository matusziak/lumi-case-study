# Lumi case study

Let's assume 3 main entities:

- A `Client` is a a therapist's customer.
- A `Product` is something a therapist offers to their clients - for example a Classic Therapy, Group Therapy, Coaching, etc.
- A `Session` represents a calendar time slot, a meeting that a client attends with the therapist to talk and get some guidance.

```typescript
// Common types definition for re-usability
type PaymentMethod = "card" | "paypal" | "bank-transfer";
type PaymentFinalization = "before" | "after"; // Client pays before or after the session
type Location = "online" | "in-person";

// Main entities
type Client = {
  id: string;
  name: string;
  discount: string;
  paymentMethodPreference: PaymentMethod;
  locationPreference: Location;
  generateInvoices: boolean;
};

type Product = {
  id: string
  name: string
  durationMinutes: number;
  price: string;
  paymentFinalization: PaymentFinalization;
};

type Session = {
  id: string;
  clientId: string;
  productId: string;
  name: string;
  date: Date;

  // Defaults from the Product
  durationMinutes: number;
  price: string;
  paymentFinalization: PaymentFinalization;

  // Defaults from the Client
  discount: string; // flat value in EUR
  paymentMethod: PaymentMethod;
  location: Location;
  generateInvoice: boolean;
};
```

## Tasks

1. Create a typescript + react project via a tool of your choice. Recommended - [vite.js](https://vitejs.dev/guide/) or [next.js](https://nextjs.org/docs/pages/building-your-application/configuring/typescript). You can skip to the second step directly since they offer full guides there, but it's always a good idea to understand the tool you use.

2. Setup tailwind css and shadcn/ui - https://ui.shadcn.com/docs/installation - and use shadcn/ui components + styling with tailwind css in the entire project.

3. Add typescript models from this file to your project and create mock data for each of them. AI is pretty good with creating mock data.

4. Create a `Sessions` component that will display a all of the sessions.

5. Create an `AddSession` component that will allow you to:

- pick the `Client` and the `Product`,
- adjust all session values,
- schedule in for a specific date,
- confirm to add and see the new session in the `Sessions` UI.

The UI/UX and styling of this app is up to you, use components you find appropriate. The data does not need any persistance, `useState` is sufficient, new sessions can be reset on page reload.
