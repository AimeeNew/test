# test
No Description

import java.util.logging.*;
import java.io.*;
class MyException extends Exception{
	MyException(){}
	MyException(String msg){super(msg);}
}
class LoggingException extends Exception{
	private static Logger logger = Logger.getLogger("LoggingException");
	public LoggingException() {
		StringWriter trace = new StringWriter();
		printStackTrace(new PrintWriter(trace));
		logger.severe(trace.toString());
	}
}
class FullConstructors{
	public static void main(String args []) {
		
		//repariedException();
		Logging();
		
	}
	public static void Logging() {
		try {
			throw new LoggingException();
		}catch(LoggingException  e) {
			System.err.println("Caught"+e);
		}
		try {
			throw new  LoggingException();
		}catch(LoggingException e) {
			System.err.println("Caught"+e);
		}
	}
	
	
	
	
	
	
	public static void f() throws MyException {
		System.out.println("Throwing Exception from f()");
		throw new MyException();
	}
	public static void g() throws MyException{
		System.out.println("Throwing Exception from g()");
		throw new MyException("Oringinated in g()");
		
	}
	public static void testfg(){
		try {
			f();
		}catch(MyException e) {
			e.printStackTrace(System.out);
		}
		try {
			g();
		}catch (MyException e) {
			e.printStackTrace(System.out);
			
		}
	}
	public static void repariedException() {
		int [] a = new int [2];
		int x = 5;
		while(true) {
			try {
				a[x] = 5;
				System.out.println(a[x]);
				break;
			}catch(ArrayIndexOutOfBoundsException  e) {
					System.err.println("Caught ArrayIndexOutOfBoundsException");
					e.printStackTrace();
					x--;
					
			}finally {
				System.out.println("are we yet ?");
			}
			
		}
		System.out.println("we have done");
	}
	
	
}
