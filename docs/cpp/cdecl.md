---
title: "__cdecl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__cdecl"
  - "__cdecl_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__cdecl 關鍵字 [C++]"
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# __cdecl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 `__cdecl` 是 C 和 C\+\+ 程式的預設呼叫慣例。  因為堆疊是由呼叫端清除，所以它可以執行 **vararg** 函式。  由於 `__cdecl` 呼叫慣例會要求每個函式呼叫都包含堆疊清除程式碼，因此它會建立比 [\_\_stdcall](../cpp/stdcall.md) 更大的可執行檔。  下列清單會顯示這個呼叫慣例的實作。  
  
|元素|實作|  
|--------|--------|  
|引數傳遞順序|由右至左。|  
|堆疊維護責任|呼叫函式會從堆疊取出引數。|  
|名稱裝飾慣例|除了匯出使用 C 連結的 \_\_cdecl 函式以外，底線字元 \(\_\) 會當做名稱的前置字元。|  
|大小寫轉譯慣例|未執行大小寫轉譯。|  
  
> [!NOTE]
>  如需相關資訊，請參閱[裝飾名稱](../build/reference/decorated-names.md)。  
  
 請將 `__cdecl` 修飾詞放置在變數或函式名稱前面。  由於 C 命名和呼叫慣例都是預設值，因此，除非您指定了 **\/Gv** \(vectorcall\)、**\/Gz** \(stdcall\) 或 **\/Gr** \(fastcall\) 編譯器選項，否則在 x86 程式碼中不需使用 `__cdecl`。  [\/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) 編譯器選項會強制執行 `__cdecl` 呼叫慣例。  
  
 在 ARM 和 x64 處理器中，編譯器會接受 \(但通常會忽略\) `__cdecl`。  ARM 和 x64 的慣例會盡可能在暫存器中傳遞引數，並在堆疊上傳遞後續的引數。  在 x64 程式碼中，請使用 `__cdecl` 覆寫 **\/Gv** 編譯器選項並使用預設的 x64 呼叫慣例。  
  
 對於非靜態類別函式，如果函式是以非正規的方式定義，則不需要在非正規定義上指定呼叫慣例修飾詞。  也就是說，對於類別非靜態成員方法而言，宣告時所指定的呼叫慣例是在定義時假設。  如果已指定此類別定義：  
  
```cpp  
struct CMyClass {  
   void __cdecl mymethod();  
};  
```  
  
 這個：  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 相當於這個：  
  
```cpp  
void __cdecl CMyClass::mymethod() { return; }  
```  
  
## 範例  
 在下列範例中，編譯器收到的指示是針對 `system` 函式使用 C 命名及呼叫慣例。  
  
```cpp  
// Example of the __cdecl keyword on function  
int __cdecl system(const char *);  
// Example of the __cdecl keyword on function pointer  
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
## 請參閱  
 [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)