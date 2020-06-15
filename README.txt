
@Documented
@Target({ElementType.METHOD, ElementType.FIELD})
@Retention(RetentionPolicy.RUNTIME)
@Constraint(validatedBy = AfterDateValidator.class)
public @interface AfterDate {
    String message() default "{Date should not be a past date}";
    Class<?>[] groups() default {};
    Class<? extends Payload>[] payload() default {};
}


public class AfterDateValidator implements ConstraintValidator<AfterDate, Date> {
    public void initialize(AfterDate constraint) {
    }

    public boolean isValid(Date obj, ConstraintValidatorContext context) {
        DateFormat dateFormat = new SimpleDateFormat("yyyy/MM/dd HH:mm:ss");
        Date date = new Date();
        dateFormat.format(date);
        return obj.after(date);
        //return false;
    }
}
