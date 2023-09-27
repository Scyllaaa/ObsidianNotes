
Instance methds are functions which can be called on objects or instances.
Instance methods must accept a reference to the actual instance on which the method was called as the first argument, by convention this argument is always called self.

When we call an instance method, we do not provider the instance for the actual argument self in the argument list. This is because the standard method invocations form with a dot, `object.method` is simply syntactic sugar for `object.method(instance)`