# DIMENSION_Dev-week2
using UnityEngine;

public class Movement2D : MonoBehaviour
{
    public class Code : MonoBehaviour
    {
        private void Awake()
        {
            Debug.Log("게임을 시작하면 Awake() 메소드에 있는 내용이 1회 실행된다.");

            Debug.Log("Debug.Log() 괄호 내부에 작성한 내용은 Console View에 출력된다.");
        }
    }

    private float moveSpeed = 5.0f; // 이동 속도
    private Vector3 moveDirection = Vector3.zero; // 이동 방향
   
    private void Update()
    {
        // Negative left, a : -1
        // Positive right, d : 1
        // Non : 0
        float x = Input.GetAxisRaw("Horizontal"); // 좌우 이동
        // Negative down, s : -1
        // Positive up, w : 1
        // Non : 0
        float y = Input.GetAxisRaw("Vertical"); // 위아래 이동

        // 이동방향 설정
        moveDirection = new Vector3(x, y, 0);

        // 새로운 위치 = 현재 위치 + (방향*속도)
        transform.position += moveDirection * moveSpeed * Time.deltaTime;


    }

    void OnCollisionEnter2D(Collision2D other)
    {
        Debug.Log("충돌 감지");
    }


}