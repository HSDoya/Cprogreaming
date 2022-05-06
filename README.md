//playerMove
#using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerMove : MonoBehaviour
{
    public float Speed = 3f;
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
   
        void Update()
        {
            Move();

        }
        private void Move()
        {
            if (Input.GetKey(KeyCode.W))
            {
                transform.Translate(Vector2.up * Speed * Time.deltaTime);
            }
            if (Input.GetKey(KeyCode.S))
            {
                transform.Translate(Vector2.down * Speed * Time.deltaTime);
            }
            if(Input.GetKey(KeyCode.D))
             {
                transform.Translate(Vector2.right * Speed * Time.deltaTime);
            }
            if(Input.GetKey(KeyCode.A))
             {
                transform.Translate(Vector2.left * Speed * Time.deltaTime);
            }

        }
    
}

//input system
 private Playermovement playerinput;
    private Rigidbody2D rb;
    [SerializeField] private float speed = 10f;
    
    void Awake()
    {
        playerinput = new Playermovement();
        rb = GetComponent<Rigidbody2D>();
       
    }
    
    private void OnEnable()
    {
        playerinput.Enable();
    }

    private void OnDisable()
    {
        playerinput.Disable();
    }
   
    void FixedUpdate()
    {
        Vector2 moveinput = playerinput.movement.move.ReadValue<Vector2>();
        rb.velocity = moveinput * speed;
        
    }
