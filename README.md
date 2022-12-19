# D365FO-OpenApiDocGenerator
Open Api Doc Generator para custom services in D365 Finance and operations


For Request and Response document for the D365FO service Operations, change your Contract Data by adding a method with a return of a variable Str (String) and name MekeSample, inside this method create an instance of the type of the class, fill it with the necessary values for the data structure , after that serialize your instance using the JsonFormSerializer chass an example below (return a static json String if you prefer, but only check if represent your structure of data). Making this change in your code, during the process of documentation of your service groups this samples of data will be available for the test inside applications like swagger docs. Default values inside your service operations will be automatic used in examples. 

```
[DataContractdata("MyContractData")]
public class MyContractData 
{
    AccountNum accountnum;
    //...
    
    
    [DataContractAttribute("accountNum")]
    public AccountNum parmAccountnum(accountnum _accountnum = accountnum)
    {
      accountnum = _accountnum;
      return accountnum;
    }
    ...

    public str MakeSample()
    {
        str jsonSample;
        MyContractData obj = new MyContractData();
        obj.pamAccounNum("USMT-000010");
        
        ...
        
        try
        {
            jsonSample = FormJsonSerializer::serializeClass(obj);
            return jsonSample;
            
        }
        catch
        {
            obj = new new MyContractData();
            jsonSample = FormJsonSerializer::serializeClass(obj);
        }


        return jsonSample;
    }

}
```



