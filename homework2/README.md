Homework 2
---

**1、简答并用程序验证**  

 * **游戏对象运动的本质是什么？**  
    游戏对象运动的本质是Transform，包括位置、角度以及大小的变化。  
    
 * **请用三种方法以上方法，实现物体的抛物线运动。（如，修改Transform属性，使用向量Vector3的方法…）**  
    * 方法一  
    通过改变游戏对象的position属性来实现抛物线运动，在水平方向上以固定速度实现匀速运动，在竖直方向上以均匀变速实现运动。  
    ```c#  
    public class Parabola : MonoBehaviour {  

        public float speed = 1;

      // Update is called once per frame
      void Update () {
            this.transform.position += Vector3.right * Time.deltaTime * 3;
            this.transform.position += Vector3.up * Time.deltaTime * (50 - speed++) / 10;
      }
    }
    ```  
    * 方法二  
    通过通过创建并定义一个新的Vector3,水平方向值固定，竖直方向值均匀变化,将新的Vector3用于改变物体的position属性，实现抛物线运动。  
    ```c#  
    public class Parabola : MonoBehaviour {

        public float speed = 1;

    	// Update is called once per frame
    	void Update () {
            Vector3 para = new Vector3(Time.deltaTime * 3, Time.deltaTime * (50 - speed++) / 10, 0);
            this.transform.position += para;
    	}
    }
    ```  
    * 方法三  
    同样使用方法二中的Vector3，然后使用Transform中的Translate方法，实现抛物线移动  
    ```c#  
    public class Parabola : MonoBehaviour {  

        public float speed = 1;
        
    	// Update is called once per frame
    	void Update () {
            Vector3 para = new Vector3(Time.deltaTime * 3, Time.deltaTime * (50 - speed++) / 10, 0);
            this.transform.Translate(para);
            
    	}
    }
    ```  
 

 * **写一个程序，实现一个完整的太阳系，其他星球围绕太阳的转速必须不一样，且不在一个法平面上。**    
   代码如下  
  ```c#  
  public class Solar : MonoBehaviour {

      public Transform Sun;
      public Transform Mercury;
      public Transform Venus;
      public Transform Earth;
      public Transform Mars;
      public Transform Jupiter;
      public Transform Saturn;
      public Transform Uranus;
      public Transform Neptune;


      // Use this for initialization
      void Start() {
          Sun.position = Vector3.zero;
          Mercury.position = new Vector3(6, 0, 0);
          Venus.position = new Vector3(9, 0, 0);
          Earth.position = new Vector3(12, 0, 0);
          Mars.position =  new Vector3(15, 0, 0);
          Jupiter.position = new Vector3(18, 0, 0);
          Saturn.position = new Vector3(23, 0, 0);
          Uranus.position = new Vector3(27, 0, 0);
          Neptune.position = new Vector3(31, 0, 0);
      }
      
      
      // Update is called once per frame
      void Update () {
          Mercury.transform.RotateAround(Vector3.zero, new Vector3(0, 10, 1), 30 * Time.deltaTime);
          Venus.transform.RotateAround(Vector3.zero, new Vector3(0, 10, 2), 28 * Time.deltaTime);
          Earth.transform.RotateAround(Vector3.zero, new Vector3(0, 20, 3), 25 * Time.deltaTime);
          Mars.transform.RotateAround(Vector3.zero, new Vector3(0, 20, 5), 22 * Time.deltaTime);
          Jupiter.transform.RotateAround(Vector3.zero, new Vector3(0, 10, 3), 20 * Time.deltaTime);
          Saturn.transform.RotateAround(Vector3.zero, new Vector3(0, 30, 3), 16 * Time.deltaTime);
          Uranus.transform.RotateAround(Vector3.zero, new Vector3(0, 30, 4), 12 * Time.deltaTime);
          Neptune.transform.RotateAround(Vector3.zero, new Vector3(0, 50, 4), 10 * Time.deltaTime);

          Mercury.Rotate(Vector3.up * 50 * Time.deltaTime);
          Venus.Rotate(Vector3.up * 30 * Time.deltaTime);
          Earth.Rotate(Vector3.up * 30 * Time.deltaTime);
          Mars.Rotate(Vector3.up * 30 * Time.deltaTime);
          Jupiter.Rotate(Vector3.up * 30 * Time.deltaTime);
          Saturn.Rotate(Vector3.up * 30 * Time.deltaTime);
          Uranus.Rotate(Vector3.up * 30 * Time.deltaTime);
          Neptune.Rotate(Vector3.up * 30 * Time.deltaTime);
      }

  }
  ```  
  效果如图    

  ![太阳系演示效果图](https://images-cdn.shimo.im/eamcTOP5OYcwhdj1/image.png!thumbnail)




