# Text-to-Website-CampEdUI

This project is an AI-powered webpage generator that translates natural language prompts into **Next.js JSX code** using components **exclusively from [CampEd UI](https://ui.camped.academy/docs/components)**. The goal is to enable rapid UI development with clean, accessible, and consistent component usage.

---

## Features

-  Converts plain-English prompts into JSX code
-  Uses only **CampEd UI** components
-  Supports **Tailwind CSS** layout
-  Valid JSX for **Next.js** pages
-  Uses **DeepSeek-Coder** for code generation
-  Includes import management and component inference

---

## How It Works

1. You provide a description like:
   ``` Create a login page with email input, password input, and a submit button ```
2. The system:
- Infers required CampEd UI components
- Builds the appropriate 'import' block
- Passes context + your prompt to a language model
- Returns complete JSX code

3. Output can be copied directly into a Next.js file like 'page.tsx'.

   ---

## Model Used

- **Name:** `deepseek-ai/deepseek-coder-1.3b-instruct`
 **Why this model?**
- Tuned for instruction-based **code generation**
- Lightweight enough to run with **8-bit quantization**
- Strong performance on JSX and TypeScript
- **No fine-tuning required** — behavior is driven by prompt engineering and examples.


## CampEd UI Integration

- Component usage is constrained to **only what’s supported** by CampEd UI.
- Imports are auto-generated based on prompt inference.
- A component cheatsheet (parsed from a '.txt' file) ensures output accuracy and restricts raw HTML usage.

---

## Example
### INPUT:
 ``` Create a login page with email input, password input, and a submit button ```
### OUTPUT:

Here is a simple component for a login page using the components from Camped UI:

```jsx
import { Button } from "@camped-ui/button"
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from "@camped-ui/card"
import { Input } from "@camped-ui/input"
import { Label } from "@camped-ui/label"
import { PasswordInput } from "@camped-ui/password-input"

export function LoginPage() {
  return (
    <Card className="w-[350px]">
      <CardHeader>
        <CardTitle>Login</CardTitle>
        <CardDescription>Please enter your credentials to access the system.</CardDescription>
      </CardHeader>
      <CardContent>
        <form>
          <div className="grid w-full items-center gap-4">
            <div className="flex flex-col space-y-1.5">
              <Label htmlFor="email">Email</Label>
              <Input id="email" placeholder="Your email" />
            </div>
            <div className="flex flex-col space-y-1.5">
              <Label htmlFor="password">Password</Label>
              <PasswordInput placeholder="********" />
            </div>
          </div>
          <Button type="submit">Submit</Button>
        </form>
      </CardContent>
    </Card>
  )
}
```

This will create a login page with email and password inputs and a submit button. The password input field is set to "password" type to hide the input. You can replace these inputs with your own components or use components from another library if required.

---
