# 예외(Exception)
> * 예외란?
>> * "Exception event" 의 약자이다
>> * 프로그램 실행 중 예외 경우가 발생하여 비정상적으로 종료되거나 잘못 작동되는 상황이다.

> * 예외처리란?
>> * 프로그램 실행 중 예외 경우가 발생경우 비정상적으로 종료되는 것을 방지하기 위함이다.

# 예외(Exception) 클래스 구조
>Object - [I] Throwable
>>* error

>>* Exception
>>>* RuntimeException

# 예외(Exception) 종류(RuntimeException)
AnnotationTypeMismatchException,  ArrayStoreException, BufferOverflowException, BufferUnderflowException, CannotRedoException, CannotUndoException,  CMMException, ConcurrentModificationException, DataBindingException, DOMException, EmptyStackException, EnumConstantNotPresentException, EventException, FileSystemAlreadyExistsException, FileSystemNotFoundException, IllegalArgumentException, IllegalMonitorStateException, IllegalPathStateException, IllegalStateException, IllformedLocaleException, ImagingOpException, IncompleteAnnotationException,  JMRuntimeException, LSException, MalformedParameterizedTypeException, MirroredTypesException, MissingResourceException,  NoSuchElementException, NoSuchMechanismException,  ProfileDataException, ProviderException, ProviderNotFoundException, RasterFormatException, RejectedExecutionException, SecurityException, SystemException, TypeConstraintException, TypeNotPresentException, UndeclaredThrowableException, UnknownEntityException, UnmodifiableSetException, UnsupportedOperationException, WebServiceException, WrongMethodTypeException, __ArithmeticException__,__ClassCastException__, __IndexOutOfBoundsException__,__NegativeArraySizeException__, __NullPointerException__,__OutOfMemoryException__, __NoClassDefFoundException__,__NumberFormatException__, __InputMismatchException__,__IOException__


# 예외 생성하기

함수(매소드 기준)

사용자 정의 예외

Exception/Runtime Exception


### 여러가지 예외를 동시에 처리하는 방법

Exceotion(부모클래스)

Runtime Exception(자식 클래스)
- ArithmeticException
- ....
- IOException

등등의 모든 예외를 Exception 객체로 받게되면 여러가지 예외를 동시에 처리할 수 있다.


성적 클래스
성적 예외 클래스
