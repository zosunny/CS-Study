# Process

---

<aside>
  
π‘ μ΄μμ²΄μ λ‘λΆν° μμμ ν λΉλ°λ **μμμ λ¨μ**

</aside>

- λλ¦½λ λ©λͺ¨λ¦¬ κ³΅κ°μ ν λΉλ°μ νλ‘κ·Έλ¨μ μ€ννλ **μμ**μ μννλ νλμ μΈμ€ν΄μ€

![Processμ λ©λͺ¨λ¦¬ μμ­](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c7f77ceb-d6e4-49b4-9ab7-afe512195829/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221108%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221108T051434Z&X-Amz-Expires=86400&X-Amz-Signature=968db8a113c0db83b299d4e3cc2e00dba2d1e975cb5ee35fd4f9a58b2e9408fe&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

`Processμ λ©λͺ¨λ¦¬ μμ­([https://gmlwjd9405.github.io/2018/09/14/process-vs-thread.html](https://gmlwjd9405.github.io/2018/09/14/process-vs-thread.html))`


- κ° νλ‘μΈμ€ λ©λͺ¨λ¦¬λ€μ λ€λ₯Έ νλ‘μΈμ€μ λ©λͺ¨λ¦¬μ λΆλ¦¬λμ΄ μ κ·Όν  μ μλ€.
    
    β νλ‘μΈμ€ κ° ν΅μ  (IPC : Inter-Process Communication)μ μ¬μ©νλ©΄ μ κ·Ό κ°λ₯
    

# Thread

---

<aside>
π‘ ν λΉλ°μ μμμ μ΄μ©νλ **μ€ν νλ¦μ λ¨μ**

</aside>

- νλ‘μΈμ€μμμ **νΉμ  μν κ²½λ‘μ νλ¦**μ μλ―Έ β μ¬μ€μ νλ‘μΈμ€μ ν¬ν¨λμ΄ μλ λ¨μλΌκ³  λ³Ό μ μμ
- νλμ νλ‘μΈμ€λ μ΅μ νλμ μ€λ λλ₯Ό κ°κ³  μμ(main thread)

![Threadμ λ©λͺ¨λ¦¬ μμ­](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/91b0d4f8-0e0c-45f2-96ad-8f897a65efb7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221108%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221108T051514Z&X-Amz-Expires=86400&X-Amz-Signature=2add06fc27afa6cddbc38399655c16ae6ab721f111e73cff209d4eb76a3f5274&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

`Threadμ λ©λͺ¨λ¦¬ μμ­([https://gmlwjd9405.github.io/2018/09/14/process-vs-thread.html](https://gmlwjd9405.github.io/2018/09/14/process-vs-thread.html))`

- stack μμ­μ μ μΈνκ³ λ λ©λͺ¨λ¦¬λ₯Ό κ³΅μ νμ¬ μ¬μ©νκΈ° λλ¬Έμ, κ° μ€λ λμ μ€νμ΄ μλ‘μκ² μν₯μ λΌμΉ¨

## multi tasking(process) vs multi thread

- **multi tasking**
    - νλμ os μμμ μ¬λ¬ νλ‘μΈμ€κ° λ³λ ¬μ μΌλ‘ μ€ν
    - (+) : κ° νλ‘μΈμ€λ λλ¦½μ μΌλ‘ λμνλ―λ‘, νλμ λ¬Έμ κ° μκΈ°λλΌλ λ€λ₯Έ νλ‘μΈμ€λ€μκ²λ μν₯μ λΌμΉμ§ μμ
    - (-) : **context switching** κ³Όμ μμ μ€λ²ν€λκ° λ°μν  μ μμ
- **multi thread**
    - νλμ νλ‘μΈμ€ μμμ νλμ μμμ μ¬λ¬ μ€λ λλ₯Ό μ¬μ©νμ¬ λμμ μ²λ¦¬
    - (+)
        
        stackμμ­μ μ μΈνκ³ λ λ©λͺ¨λ¦¬ κ³΅μ κ° μΌμ΄λκΈ°μ μμμ ν¨μ¨μ μΈ μ΄μ©μ΄ κ°λ₯νκ³ 
        
        μ€λ λ κ° λ°μ΄ν°μ μ λ¬μ΄ μ©μ΄ν΄ ν΅μ μ λΆλ΄μ΄ λνλ©°
        
        μλ΅ μκ°μ΄ λΉ λ₯΄λ€.
        
    - (-)
        
        μμμ κ³΅μ νκΈ°μ **λκΈ°ν λ¬Έμ **κ° λ°μν  μ μλ€.
        
        λλ²κΉμ΄ κΉλ€λ‘­λ€.
        

β π©Β λ³΄ν΅μ λ©ν° νλ‘μΈμ€ λμ  λ©ν° μ€λ λκ° μ¬μ©λλ€. (νλμ νλ‘κ·Έλ¨ μμμ μ¬λ¬ λμ-μμμ μν)

νλ‘μΈμ€ κ°μ context switchingμ μ€λ²ν€λκ° μ μΌ ν° μ΄μ 

> β **context switching**
νλ‘μΈμ€μ μ νμ΄ μΌμ΄λ  λ, μ΄μ μ λμνλ νλ‘μΈμ€μ μν(context)λ₯Ό λ³΄κ΄νκ³ , λ€μ μμλ‘ λμνλ νλ‘μΈμ€λ₯Ό μν΄ λ³΄κ΄λ contextλ₯Ό λ³΅κ΅¬νλ μμ
> 

[Thread-safe] 

- μ€λ λλ€μ΄ κ°μ λ°μ΄ν°μ μ κ·Όνλ―λ‘μ¨ μκΈ°λ λμμ± λ¬Έμ λ₯Ό ν΄κ²°νκΈ° μν¨
- μ¬λ¬ μ€λ λμμ νΉμ  λ°μ΄ν°μ λμ μ κ·Όνμ¬ μ¬μ©νλλΌλ μμ νκ³  μ ννκ² λμνλλ‘ ν¨

### Reference

[https://velog.io/@raejoonee/νλ‘μΈμ€μ-μ€λ λμ-μ°¨μ΄](https://velog.io/@raejoonee/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%99%80-%EC%8A%A4%EB%A0%88%EB%93%9C%EC%9D%98-%EC%B0%A8%EC%9D%B4)
