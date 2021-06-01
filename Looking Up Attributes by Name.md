Looking Up Attributes by Name
        - We see a [[dot expression]] in order to evaluate a [[dot expression]]
            - 1. We evaluate the `<expression>` to the left of the dot, which yields the object of the [[dot expression]]
            - 2. `<name>` is matched against the instance attributes of that object; **If an attribute with the name exists,** its value is returned
            - 3. If not, <name> is looked up in the class, which yields a class attribute value.
            - 4. That value is returned **unless it is a function,** in which case a [[bound method]] is returned instead.
                - **unless it is a function,** like, `withdraw` or `deposit`
                - This case a [[bound method]] is returned instead
                    - The object of the [[dot expression]] is bound together with that function to create a [[bound method]]