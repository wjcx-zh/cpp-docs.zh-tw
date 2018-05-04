---
title: __stdcall |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __stdcall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f018a87f7a73de6500294b0817263e6f847af8ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="stdcall"></a>__stdcall
**Microsoft 特定的**  
  
 `__stdcall` 呼叫慣例用於呼叫 Win32 API 函式。 被呼叫端會清除堆疊，因此編譯器會建立**vararg**函式`__cdecl`。 使用這個呼叫慣例的函式需要函式原型。  
  
## <a name="syntax"></a>語法  
  
```  
  
return-type __stdcall function-name[(argument-list)]  
```  
  
## <a name="remarks"></a>備註  
 下列清單會顯示這個呼叫慣例的實作。  
  
|項目|實作|  
|-------------|--------------------|  
|引數傳遞順序|由右至左。|  
|引數傳遞慣例|以傳值方式，除非傳遞指標或參考類型。|  
|堆疊維護責任|被呼叫函式會從堆疊快顯其本身的引數。|  
|名稱裝飾慣例|名稱前面會加底線 (_)。 名稱後面加上 @ 符號，再接著引數清單中的位元組數目 (十進位)。 因此，宣告為 `int func( int a, double b )` 的函式會裝飾為如下：`_func@12`|  
|大小寫轉譯慣例|無|  
  
 [/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md)編譯器選項會指定`__stdcall`所有未以不同呼叫慣例明確宣告的函式。  
  
 使用宣告的函式`__stdcall`修飾詞的傳回值做為使用宣告的函式的相同方式[__cdecl](../cpp/cdecl.md)。  
  
 在 ARM 和 x64 處理器上，編譯器會接受並忽略 `__stdcall` 關鍵字；在 ARM 和 x64 結構上，依照慣例，引數會盡可能在暫存器中傳遞，而後續引數會在堆疊上傳遞。  
  
 對於非靜態類別函式，如果函式是以非正規的方式定義，則不需要在非正規定義上指定呼叫慣例修飾詞。 也就是說，對於類別非靜態成員方法而言，宣告時所指定的呼叫慣例是在定義時假設。 如果已指定此類別定義，  
  
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
  
## <a name="example"></a>範例  
 在下列範例中，使用 __**stdcall**會導致所有`WINAPI`函式類型被當成標準呼叫處理：  
  
```cpp  
// Example of the __stdcall keyword  
#define WINAPI __stdcall  
// Example of the __stdcall keyword on function pointer  
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
## <a name="see-also"></a>另請參閱  
 [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)   
 [關鍵字](../cpp/keywords-cpp.md)