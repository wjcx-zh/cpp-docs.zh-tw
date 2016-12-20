---
title: "__stdcall | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__stdcall_cpp"
  - "__stdcall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__stdcall 關鍵字 [C++]"
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __stdcall
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 `__stdcall` 呼叫慣例用於呼叫 Win32 API 函式。  被呼叫端會清除堆疊，因此編譯器會建立 **vararg** 函式 `__cdecl`。  使用這個呼叫慣例的函式需要函式原型。  
  
## 語法  
  
```  
  
return-type __stdcall function-name[(argument-list)]  
```  
  
## 備註  
 下列清單會顯示這個呼叫慣例的實作。  
  
|元素|實作|  
|--------|--------|  
|引數傳遞順序|由右至左。|  
|引數傳遞慣例|以傳值方式，除非傳遞指標或參考類型。|  
|堆疊維護責任|被呼叫函式會從堆疊快顯其本身的引數。|  
|名稱裝飾慣例|名稱前面會加底線 \(\_\)。  名稱後面加上 @ 符號，再接著引數清單中的位元組數目 \(十進位\)。  因此，宣告為 `int func( int a, double b )` 的函式會裝飾為如下：`_func@12`|  
|大小寫轉譯慣例|無|  
  
 [\/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md) 編譯器選項會為所有未以不同呼叫慣例明確宣告的函式指定 `__stdcall`。  
  
 使用 `__stdcall` 修飾詞宣告的函式傳回值的方式與使用 [\_\_cdecl](../cpp/cdecl.md) 宣告的函式相同。  
  
 在 ARM 和 x64 處理器上，編譯器會接受並忽略 `__stdcall` 關鍵字；在 ARM 和 x64 結構上，依照慣例，引數會盡可能在暫存器中傳遞，而後續引數會在堆疊上傳遞。  
  
 對於非靜態類別函式，如果函式是以非正規的方式定義，則不需要在非正規定義上指定呼叫慣例修飾詞。  也就是說，對於類別非靜態成員方法而言，宣告時所指定的呼叫慣例是在定義時假設。  如果已指定此類別定義，  
  
```cpp  
struct CMyClass {  
   void __stdcall mymethod();  
};  
```  
  
 this  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 相當於這個  
  
```cpp  
void __stdcall CMyClass::mymethod() { return; }  
```  
  
## 範例  
 在下列範例中，使用 \_\_**stdcall** 會導致將所有 `WINAPI` 函式類型被當成標準呼叫處理：  
  
```c  
// Example of the __stdcall keyword  
#define WINAPI __stdcall  
// Example of the __stdcall keyword on function pointer  
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
## 請參閱  
 [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)