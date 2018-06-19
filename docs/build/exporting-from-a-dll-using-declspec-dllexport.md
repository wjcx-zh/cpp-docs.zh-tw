---
title: 從 DLL 使用 __declspec （dllexport） 匯出 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- dllexport
- __declspec
dev_langs:
- C++
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6ab1d11c117c75633ce4ab836965449c4cc6ca1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368544"
---
# <a name="exporting-from-a-dll-using-declspecdllexport"></a>使用 __declspec(dllexport) 從 DLL 匯出
導入的 Microsoft **__export** 16 位元編譯器版本的 Visual c + + 允許編譯器自動產生匯出名稱，並將它們放在.lib 檔案。 然後就像靜態.lib 連結 DLL 使用這個.lib 檔案。  
  
 在較新的編譯器版本中，您可以匯出資料、 函數、 類別或類別成員函式使用 **__declspec （dllexport)** 關鍵字。 **__declspec （dllexport)** 匯出指示詞加入物件檔案，讓您不需要使用.def 檔。  
  
 嘗試匯出裝飾 c + + 函式名稱時，最明顯這種便利性。 因為沒有標準的規格名稱裝飾，匯出的函式的名稱可能會變更的編譯器版本之間。 如果您使用 **__declspec （dllexport)**，重新編譯的 DLL 和相依的.exe 檔案是必要的帳戶，才能找出任何命名慣例的變更。  
  
 許多匯出指示詞，例如可只在.def 檔案中，序數、 NONAME 和私用，而且沒有任何方法來指定這些屬性不使用.def 檔案。 不過，使用 **__declspec （dllexport)** 除了使用.def 檔案不會造成建置錯誤。  
  
 若要匯出函式， **__declspec （dllexport)** 關鍵字必須出現左邊的呼叫慣例關鍵字，如果指定的關鍵字。 例如:   
  
```  
__declspec(dllexport) void __cdecl Function1(void);  
```  
  
 若要匯出的所有公用資料成員和類別中的成員函式，關鍵字必須出現在類別名稱的左邊，如下所示：  
  
```  
class __declspec(dllexport) CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
> [!NOTE]
>  `__declspec(dllexport)` 無法套用至函式`__clrcall`呼叫慣例。  
  
 當建置您的 DLL，您通常可以建立包含函式原型和/或您匯出，並加入的類別的標頭檔 **__declspec （dllexport)** 標頭檔中宣告。 若要讓您的程式碼更容易閱讀，定義 巨集 **__declspec （dllexport)** ，您要匯出的每個符號會使用巨集：  
  
```  
#define DllExport   __declspec( dllexport )   
```  
  
 **__declspec （dllexport)** 存放區函式之 DLL 匯出資料表中的名稱。 如果您想要最佳化的資料表大小，請參閱[從根據序數而非依名稱的 DLL 匯出函式](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。  
  
> [!NOTE]
>  當將移植從 Win16 到 Win32 的 DLL 原始碼，來取代每個執行個體 **__export**與 **__declspec （dllexport)**。  
  
 做為參考，搜尋透過 Win32 Winbase.h 標頭檔。 它包含的範例 **__declspec （dllimport)** 使用量。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [使用.def 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [匯出和匯入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [匯出 c + + 函式，以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [匯出 C 函式，以用於 C 或 c + + 語言可執行檔](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [決定要使用哪一個匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [匯入應用程式使用 __declspec （dllimport）](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [__Declspec 關鍵字](../cpp/declspec.md)  
  
-   [匯入和匯出內嵌函式](../build/importing-and-exporting-inline-functions.md)  
  
-   [交互匯入](../build/mutual-imports.md)  
  
## <a name="see-also"></a>另請參閱  
 [從 DLL 匯出](../build/exporting-from-a-dll.md)