

### 정적 메소드

```
  public class testRepository {
    private static Long sequence = 0L;
    Map<String, User> store = new HashMap<String, User>();
    private static testRepository one;
    
    public static testRepository getInstance() {
      if (one == null){
        one = new testRepository(); 
      }
      return one;
    }
    
  
  }

```
