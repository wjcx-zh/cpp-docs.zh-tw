---
title: "__fastcall |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __fastcall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: da4644465cf5b4df0ec4477edc1871b0b8291134
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="fastcall"></a>__fastcall
**Microsoft 特定的**  
  
 `__fastcall` 呼叫慣例會指定函式的引數應該盡可能在暫存器中傳遞。 這個呼叫慣例僅適用於 x86 架構。 下列清單會顯示這個呼叫慣例的實作。  
  
|項目|實作|  
|-------------|--------------------|  
|引數傳遞順序|引數清單中的前兩個 DWORD 引數或較小引數會由左至右傳入 ECX 和 EDX 暫存器，所有其他引數則由右至左傳遞至堆疊上。|  
|堆疊維護責任|所呼叫的函式會從堆疊取出引數。|  
|名稱裝飾慣例|名稱前面會加上 @ 符號，而參數清單中後面接著位元組數 (十進位) 的 @ 符號會加在名稱後面。|  
|大小寫轉譯慣例|未執行大小寫轉譯。|  
  
> [!NOTE]
>  未來的編譯器版本可能會使用不同的暫存器來儲存參數。  
  
 使用[/Gr](../build/reference/gd-gr-gv-gz-calling-convention.md)編譯器選項會導致編譯成模組中的每個函式`__fastcall`除非使用衝突的屬性宣告的函式或函式的名稱是`main`。  
  
 目標為 ARM 和 x64 架構的編譯器會接受並忽略 `__fastcall` 關鍵字，而按照慣例，在 x64 晶片上的前四個引數會傳入暫存器 (可能的話)，其他引數則會傳遞至堆疊上。 如需詳細資訊，請參閱[概觀 x64 呼叫慣例](../build/overview-of-x64-calling-conventions.md)。 在 ARM 晶片上，最多可以在暫存器中傳遞四個整數引數和八個浮點引數，而其他引數則是在堆疊上傳遞。  
  
 對於非靜態類別函式，如果函式是以非正規的方式定義，則不需要在非正規定義上指定呼叫慣例修飾詞。 也就是說，對於類別非靜態成員方法而言，宣告時所指定的呼叫慣例是在定義時假設。 如果已指定此類別定義：  
  
```cpp  
struct CMyClass {  
   void __fastcall mymethod();  
};  
```  
  
 這個：  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 相當於這個：  
  
```cpp  
void __fastcall CMyClass::mymethod() { return; }  
```  
  
## <a name="example"></a>範例  
 下列範例會對暫存器中的 `DeleteAggrWrapper` 函式傳遞引數：  
  
```cpp  
// Example of the __fastcall keyword  
#define FASTCALL    __fastcall  
  
void FASTCALL DeleteAggrWrapper(void* pWrapper);  
// Example of the __ fastcall keyword on function pointer  
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
**END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)   
 [關鍵字](../cpp/keywords-cpp.md)
