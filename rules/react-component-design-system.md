---
include: "*.ts,*.tsx"
title: Enforce component design system in React
tags: nextjs,react,typescript
---

All design system components must use forwardRef pattern, CVA for variants, and follow the established component structure.

Bad:

```typescript
interface ButtonProps {
  className?: string
  variant?: string
  size?: string
  children: React.ReactNode
}

const Button = ({ className, variant, size, children, ...props }: ButtonProps) => {
  let baseClasses = "inline-flex items-center justify-center rounded-md text-sm font-medium"

  if (variant === "destructive") {
    baseClasses += " bg-red-500 text-white"
  } else {
    baseClasses += " bg-blue-500 text-white"
  }

  if (size === "sm") {
    baseClasses += " h-9 px-3"
  } else {
    baseClasses += " h-10 px-4 py-2"
  }

  return (
    <button className={`${baseClasses} ${className}`} {...props}>
      {children}
    </button>
  )
}
```

Good:

```typescript
import { cva, type VariantProps } from "class-variance-authority"
import { clx } from "../utils"

const buttonVariants = cva(
  "inline-flex items-center justify-center rounded-md text-sm font-medium",
  {
    variants: {
      variant: {
        default: "bg-primary text-primary-foreground hover:bg-primary/90",
        destructive: "bg-destructive text-destructive-foreground hover:bg-destructive/90",
      },
      size: {
        default: "h-10 px-4 py-2",
        sm: "h-9 rounded-md px-3",
      },
    },
    defaultVariants: {
      variant: "default",
      size: "default",
    },
  }
)

export interface ButtonProps
  extends React.ButtonHTMLAttributes<HTMLButtonElement>,
    VariantProps<typeof buttonVariants> {}

const Button = React.forwardRef<HTMLButtonElement, ButtonProps>(
  ({ className, variant, size, ...props }, ref) => {
    return (
      <button
        className={clx(buttonVariants({ variant, size }), className)}
        ref={ref}
        {...props}
      />
    )
  }
)
Button.displayName = "Button"

export { Button, buttonVariants }
```
