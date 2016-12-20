---
title: "從 Visual Basic 應用程式中呼叫 DLL 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__stdcall 關鍵字 [C++]"
  - "從 VB 應用程式中呼叫 DLL 函式 [C++]"
  - "DLL 函式 [C++]"
  - "DLL 函式 [C++], 呼叫"
  - "DLL [C++], 呼叫"
  - "函式呼叫 [C++], DLL 函式"
  - "函式 [C++], 從 Visual Basic 呼叫 DLL 函式"
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 從 Visual Basic 應用程式中呼叫 DLL 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為了讓 Visual Basic 應用程式 \(或其他語言撰寫的應用程式，例如 Pascal 或 Fortran\) 可以呼叫 C\/C\+\+ DLL 裡的函式，函式必須由編譯器在未使用任何名稱裝飾情況下使用正確呼叫慣例匯出。  
  
 `__stdcall` 會為函式建立正確的呼叫慣例 \(呼叫函式清除堆疊並且由右至左傳遞參數\)，但以不同方式來修飾函式名稱。  因此，當 **\_\_declspec\(dllexport\)** 用於 DLL 裡的匯出函式時，會匯出裝飾名稱。  
  
 `__stdcall` 名稱裝飾會以底線 \(\_\) 附加在符號名稱之前，並且以 @ 字元附加於符號，這字元後面跟著引數清單裡的位元組數 \(所需的堆疊空間\)。  因此，當函式宣告為：  
  
```  
int __stdcall func (int a, double b)  
```  
  
 就會裝飾成：  
  
```  
_func@12  
```  
  
 C 呼叫慣例 \(`__cdecl`\) 將名稱裝飾為 `_func`。  
  
 若要取得裝飾名稱，使用 [\/MAP](../build/reference/map-generate-mapfile.md)。  使用 **\_\_declspec\(dllexport\)** 時會執行下列事項：  
  
-   匯出函式時若是用到 C 呼叫慣例 \(**\_cdecl**\)，則名稱在匯出時會移除前置底線 \(\_\)。  
  
-   匯出函式時若未用到 C 呼叫慣例 \(例如，`__stdcall`\)，便會匯出裝飾名稱。  
  
 因為沒有方法可以覆寫堆疊清除發生的地方，您必須使用 `__stdcall`。  若要以 `__stdcall` 取消裝飾名稱，您必須在 .def 檔的 EXPORTS 區段裡使用別名 \(Alias\) 來指定它們。  下列顯示函式宣告：  
  
```  
int  __stdcall MyFunc (int a, double b);  
void __stdcall InitCode (void);  
```  
  
 在 .DEF 檔案中：  
  
```  
EXPORTS  
   MYFUNC=_MyFunc@12  
   INITCODE=_InitCode@0  
```  
  
 針對以 Visual Basic 撰寫的程式所呼叫的 DLL，本主題出現的別名技術在 .def 檔裡也是必要的。  如果別名是在 Visual Basic 程式裡完成，在 .def 檔使用別名就不是必要的。  在 [Declare](../Topic/Declare%20Statement.md) 陳述式中加入別名子句，便可於 Visual Basic 程式裡完成。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [從 DLL 匯出](../build/exporting-from-a-dll.md)  
  
-   [使用 .DEF 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [匯出 C\+\+ 函式以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [決定要使用哪一個匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [裝飾名稱](../build/reference/decorated-names.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)