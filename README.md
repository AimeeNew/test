# test
No Description
//class MyException extends Exception{
//	public MyException() {}
//	public MyException(String msg) {super(msg);}
//	
//}
//class FullConstructors{
//	public static void f() throws MyException{
//		System.out.println("Throwsing MyException from f()");
//		throw new MyException();
//	}
//	public static void g() throws MyException{
//		System.out.println("Throwing MyException form g()");
//		throw new MyException("Originated in g()");
//	}
//	
//	public static void main(String args []) {
//		
//		try {
//			f();
//			
//		}catch(Exception e) {
//			e.printStackTrace(System.out);
//			
//		}
//		try {
//			g();
//			
//		}catch(Exception e) {
//			e.printStackTrace(System.out);
//			
//		}
//		
//		
//	}
//}
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
