using UnityEngine;
using System.Collections;//������ͷ�ļ�дunity�ű��ش�

public class ExampleBehaviourScript//�ļ��� : MonoBehaviour
{
    
    void Start()//����ʼʱִ��һ��
    {
        rb = GetComponent<Rigidbody>();//��ø���
    }
    void Update()
    {
         MoveDir = new Vector3(Input.GetAxis("Horizontal"), 0, Input.GetAxis("Vertical")).normalized;// ��������¼�wasd
    }
    void FixedUpdate()
    {
        rb.AddForce(MoveDir * moveSpeed);//ʵ���ƶ���AddForce������
    }
}
-----------------------------------------------------------------------------------------
public class ForeachLoop : MonoBehaviour //foreachѭ��
{   
    void Start () 
    {
        string[] strings = new string[3];
        
        strings[0] = "First string";
        strings[1] = "Second string";
        strings[2] = "Third string";
        
        foreach(string item in strings)//�����������Զ���һ
        {
            print (item);
        }
    }
}
-------------------------------------------------------------------------------------------
public class Example:MonoBehaviour
{
    public int a;//���ţ�������unity���޸�
    private int b;//˽�У����ڽű����޸�
    void Start()
    {
        myOtherClass = new AnotherClass();//���AnotherClass��ʵ��
        myOtherClass.FruitMachine(alpha, myOtherClass.apples);//���Ե���AnotherClass�п��ŵ�FruitMachine����
    }
}//��������ű���Ҫ���ã����ţ�����˽��
public class AnotherClass
{
    public int apples;
    public int bananas;

    public void FruitMachine (int a, int b)
    {
        int answer;
        answer = a + b;
        Debug.Log("Fruit total: " + answer);
    }
}
-------------------------------------------
void Awake ()
    {
        Debug.Log("Awake called.");
    }//�ű�δ������ʱҲ��������
    
    
    void Start ()
    {
        Debug.Log("Start called.");
    }//�ű�����ʱ����
//��������������ֻ����һ��
---------------------------------------------------------
    vector = player.transform.position - enemy.transform.position;//������������enemyָ��player
//���������ֱ����magnitudeģ���͵��ڵ�λ����
    float a = player.transform.position.magnitude;//magnitude���Լ���player����ڣ�0,0,0���ľ���
     ���㹫ʽ: ��λ���ȣ���1,1,1��
     Vector v1= new Vector(2,2,3);
     v1= new Vector(v1.x/v1.magnitude,v1.y/v1.magnitude,v1.z/v1.magnitude); //��λ������֮��
------------------------------------------------------
  ��ˣ�
     Vector A(a,b,c)
     Vector B(x,y,z)
     AB�ĵ�� m=(a*x)+(b*y)+(c*z)=A*B

     ��˵ļ������壺
     �õ�B��A��ͶӰ�ĳ���

     ��˵Ĵ��·�λ��
     m>0:���
     m=0:ֱ��
     m<0:�۽�

     �����;��
     �����ж϶���ķ�λ��
    ���Լ�����������֮��ļн�;
--------------------------------------------
public class EnableComponents : MonoBehaviour
{
    private Light myLight;
    
    
    void Start ()
    {
        myLight = GetComponent<Light>();//�������
    }
}
----------------------------------












unity��������˵��
public class ExampleBehaviourScript : MonoBehaviour
{
    void Awake()//���κ�start����֮ǰִ��
    {

    }
     private void OnEnable()//���ö�����������ã������ڼ��عؿ����нű�����Ϸ����
    {
        
    }
    private void OnLevelWasLoaded(int level)//�ɸ�֪��Ϸ�Ѽ����¹ؿ�
    {
        
    }


    void OnApplicationPause()//֡�Ľ�β����
    {

    }




    void Update()//ÿ֡����һ�Σ��ܵ���֡��Ӱ�죬����Ҫʵʱ���õĺ������Ŷ��˻Ῠ��
    {

    }
    void FixedUpdate()//һ�������ʮ�Σ������ȶ�
    {

    }
    void LateUpdate()//ÿ֡����һ�Σ���Update֮��ͨ�����ڵ����˳Ƹ������
    {

    }
}
-------------------------------------------
���������ű������ķ�����
1.
//A�ű�
public class Ascript : MonoBehaviour 
{
    public int value = 1; //Ascript���ڲ�����
    public void DoSomething()
    {
        Debug.Log("Ascript doing!"); //��Unity����̨����ʾ"Ascript doing!"
    }
}
//B�ű�
public class Main : MonoBehaviour 
{
    public Ascript ascript;//Ҫ����A�ű��������ȶ���
    private int Mvalue;
    public void DoASomething()
    {   
        
        if(ascript != null) //����һ���жϣ�ʹ�������ȫ�����Ϊ���ˣ��Ͳ�ִ�д˴��롣
        {
            Mvalue = ascript.value; //Mvalue = 1;
            ascript.DoSomething(); //��� Ascript doing!
        }
    }
    void Start()
    {
        DoASomething(); //��Ϸ��ʼʱ����
    }
}
����һ���ն��󣬹���A�ű����ٽ��ÿն�������B�ű���ascript��
��2��
public class Main : MonoBehaviour 
{
    public Ascript ascript;
    public void DoASomething()
    {   
       
        if(ascript != null) ascript.SendMessage("DoSomething");//Ascript�е�DoSomething�ɿ��ſ�˽��
    }
    void Start()
    {
        DoASomething();
    }
}

---------------------------------------------------
����
public class Ascript : MonoBehaviour
{
    public static Ascript aStatic;
    public int value = 1;
    void Start() 
    {
        aStatic = this;
    }
    public void DoSomething()
    {
        Debug.Log("Ascript doing!");
    }
}
public class Main : MonoBehaviour {
    private int Mvalue;
    public void DoASomething()
    {   
        Ascript.aStatic.DoSomething();//����
        Mvalue = Ascript.aStatic.value; // Mvalue = 1;
    }
    void Start()
    {
        DoASomething();
    }
}
��չ���������ģʽ
ʹ�ü�ʹ���̳���MonoBehaviour����Ҳ�����������ű�ֱ�ӵ���
���þ�̬���캯�����Start()����
public class Singleton 
{
    public static Singleton instance;
    public static Singleton Instance
    {
        get {
            if (instance==null)
            {
                instance = new Singleton();
            }
            return instance;
        }
    }
}
//����һ������ʹ�� Singleton.Instance. �Ϳ��Ե���Singleton�ڲ��ķ������߱���



public class Singleton<T> : MonoBehaviour where T : Singleton<T>//���Ʒ���
{
    public static T Instance { get; private set; }
    protected void Awake()
    {
        if (Instance == null)
        {
            Instance = (T) this;//��������
            DontDestroyOnLoad(gameObject); //��ʵ�������泡���л�������
        }
        else
        {
            Destroy(gameObject); //�����ظ�ʵ��
        }
    }
}
///<summary>
/// ��Ϸ���Ĺ���ű�
///<summary>
public class Manager : Singleton<GameManager> //�̳��ڵ������Manager
{
    public int Value { get; set; } = 0;
}
//����һ������ʹ�� Manager.Instance. �Ϳ��Ե���Manager�ڲ��ķ������߱���
//�����ڳ�����ֻ��ʵ��һ����������������gamemanager��menumanager�У������ڳ�����ֻ����һ��
-----------------------------------------------------------



�̳�
public abstract class Buff //����������Buff
{
    public enum BuffKind //����ö������ Buff����
    {
        HpBuff, //��ѪBuff
        SpeedBuff,//����Buff
    }
    public float m_Length;//Buff����ʱ��
    public BuffKind m_BuffKind;//Buff������
    public Player m_Player;//���õ�ʵ��
    public Buff(Player player, BuffKind buffKind, float length)//���캯������ 
    {
        m_Player = player; //��һ��������ʾ���õ�ʵ�� ��������ֻ����� ��������ΪPlayer ��ʵӦ������Ϊʵ��
        m_BuffKind = buffKind; //�ڶ���������ʾ����Buff������
        m_Length = length; //��������ʾ��Buff������ʱ��
    }
    public virtual void OnAdd() { }//���Buff���麯��
}
--------------------------------------------------




