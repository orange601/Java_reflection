# Java_reflection
reflection이라는 단어를 너무 오랜만에 들어서 다시 개념정리를 한다.

* 컴파일된 자바 코드에서 역으로 클래스를 불러서 메소드(Method) 및 변수(Field)를 구해오는 방법으로 클래스를 동적 로딩하여 사용할때 많이 사용되고 디컴파일할때에도 자주 사용되는 기법이다.

#### 예제
````java
package com.reflection.orange.endpoint;

import java.lang.reflect.InvocationTargetException;
import java.lang.reflect.Method;

public class Endpoint {
	public static void main(String[] args) throws ClassNotFoundException {
		
		// 클래스 조회1
        Class string = "String".getClass();
        System.out.println(string); //class java.lang.String
        
        // 클래스 조회2
        Class classname = Class.forName("com.reflection.orange.endpoint.Parent");
        System.out.println(classname);
        
        // 클래스 조회3
        Class parent = new Parent().getClass();
        System.out.println(parent);
        
        // 메서드 조회
        Method[] methods = parent.getDeclaredMethods();
        for (Method method : methods) {
            System.out.println(method.toString());
        }

        
        // 클래스 메서드 호출
        Class test = Class.forName("com.reflection.orange.endpoint.Test");
        Method[] met = test.getDeclaredMethods();
        for (Method method : met) {
            System.out.println(method.toString());
        }
        try {
        	 try {
				Object obj = test.newInstance();
				met[0].invoke(obj, 1);
			} catch (InstantiationException e) {
				e.printStackTrace();
			}
		} catch (IllegalAccessException e) {
			e.printStackTrace();
		} catch (IllegalArgumentException e) {
			e.printStackTrace();
		} catch (InvocationTargetException e) {
			e.printStackTrace();
		}



        
        Class c8 = Double.TYPE;     //double
        Class c9 = Void.TYPE;       //void
        
	}
}

````
