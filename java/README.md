```java
public class HandleUniqueConstraintViolation {

    public static void handleUniqueConstraintViolation(DataIntegrityViolationException e) {
        String message = e.getMostSpecificCause().getMessage();

        if (message != null && message.contains("duplicate key value violates unique constraint")) {
            if (message.contains("Key (name)=")) {
                throw new UniqueConstraintViolationException("Name already exists!");
            }
            throw new UniqueConstraintViolationException("A unique constraint violation occurred!");
        }
    }
}
```