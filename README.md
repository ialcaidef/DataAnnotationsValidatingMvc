# DataAnnotationsValidatingMvc
MOD06_DEMO_04

Ejemplo de validación de aplicaciones MVC  



namespace DataAnnotationsExample.Models  
{  

    public class Student  
   
    {
        public int StudentId { get; set; }

        [Display(Name = "First Name:")]
        [Required(ErrorMessage = "Please enter your first name.")]
        public string FirstName { get; set; }

        [Display(Name = "Last Name:")]
        [Required(ErrorMessage = "Please enter your last name.")]
        public string LastName { get; set; }

        [Display(Name = "Birthdate:")]
        [DataType(DataType.Date)]
        public DateTime Birthdate { get; set; }

        [Display(Name = "Are you a university student?")]
        [InUniversityValidation]
        public bool UniversityStudent { get; set; }
    }
}
    
    


namespace DataAnnotationsExample.Validators  
{  
    public class InUniversityValidationAttribute : ValidationAttribute  
      
    {  
        protected override ValidationResult IsValid(object value, ValidationContext validationContext)  
        
        {  
            Student student = (Student)validationContext.ObjectInstance;            
            if (!student.UniversityStudent)  
            {            
                return new ValidationResult("Sorry you must be a student of the university in order to submit");                
            }      
            return ValidationResult.Success;  
        }  
    }  
}  

