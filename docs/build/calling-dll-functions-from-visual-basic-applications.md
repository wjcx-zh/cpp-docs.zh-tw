---
title: 從 Visual Basic 應用程式呼叫 DLL 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9877544635dc894bbe379c751de35297add91c9d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367078"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>從 Visual Basic 應用程式中呼叫 DLL 函式
Visual Basic 應用程式 （或依照 pascal 命名法或 Fortran 等其他語言中的應用程式） C/c + + DLL 中呼叫函式，函式必須使用正確的呼叫慣例，而由編譯器所做的任何名稱裝飾不匯出。  
  
 `__stdcall` 建立正確的呼叫慣例函式 （呼叫的函式會清除堆疊和由右至左傳遞參數），但不同裝飾函式名稱。 因此， **__declspec （dllexport)** 用在 DLL 中匯出的函式，會匯出裝飾的名稱。  
  
 `__stdcall`名稱裝飾符號名稱以底線 (_)，並將附加的符號寬度 at 符號 (@) 字元，後面的引數清單 （所需的堆疊空間） 中的位元組數目。 如此一來，當宣告為函式：  
  
```  
int __stdcall func (int a, double b)  
```  
  
 裝飾為：  
  
```  
_func@12  
```  
  
 C 呼叫慣例 (`__cdecl`) 裝飾名稱與`_func`。  
  
 若要取得裝飾的名稱，請使用[對應](../build/reference/map-generate-mapfile.md)。 使用 **__declspec （dllexport)** 會進行下列作業：  
  
-   如果匯出的函式是以 C 呼叫慣例 (**_cdecl**)，它會去除前置底線 (_)，會匯出名稱時。  
  
-   如果要匯出的函式不使用 C 呼叫慣例 (例如， `__stdcall`)，它會將匯出的裝飾的名稱。  
  
 因為沒有任何方法來覆寫發生堆疊清除，您必須使用`__stdcall`。 若要快速具有名稱`__stdcall`，您必須使用別名在.def 檔的 EXPORTS 區段中指定。 這是下列函式宣告，如下所示顯示：  
  
```  
int  __stdcall MyFunc (int a, double b);  
void __stdcall InitCode (void);  
```  
  
 在中。DEF 檔案：  
  
```  
EXPORTS  
   MYFUNC=_MyFunc@12  
   INITCODE=_InitCode@0  
```  
  
 適用於 Visual Basic 中撰寫的程式被呼叫的 Dll，本主題中的別名技巧需要.def 檔案中。 如果在 Visual Basic 程式中進行設定別名，不需要使用.def 檔案中的別名。 可以在 Visual Basic 程式中完成新增別名子句[Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)陳述式。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [從 DLL 匯出](../build/exporting-from-a-dll.md)  
  
-   [匯出從 DLL 使用。DEF 檔案](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [匯出 C 語言可執行檔中使用的 c + + 函式](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [決定要使用哪一個匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [裝飾的名稱](../build/reference/decorated-names.md)  
  
## <a name="see-also"></a>另請參閱  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)