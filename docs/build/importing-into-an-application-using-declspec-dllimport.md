---
title: 將應用程式使用 __declspec （dllimport） 匯入 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- __declspec
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82974ec688fbe688c98188c2e99a54462da81165
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368830"
---
# <a name="importing-into-an-application-using-declspecdllimport"></a>使用 __declspec(dllimport) 匯入至應用程式
使用公用符號的 DLL 所定義的程式，即稱為匯入它們。 當您建立標頭檔，用於您的 Dll，建立應用程式使用 **__declspec （dllimport)** 公用符號的宣告。 關鍵字 **__declspec （dllimport)** 不論您匯出.def 檔案，或與運作方式都 **__declspec （dllexport)** 關鍵字。  
  
 若要讓您的程式碼更容易閱讀，定義 巨集 **__declspec （dllimport)** ，然後使用巨集來宣告的每個匯入的符號：  
  
```  
#define DllImport   __declspec( dllimport )  
  
DllImport int  j;  
DllImport void func();  
```  
  
 使用 **__declspec （dllimport)** 上函式宣告為選擇性，但如果您使用此關鍵字，編譯器會產生更有效率的程式碼。 不過，您必須使用 **__declspec （dllimport)** ，匯入可存取 DLL 的公用資料符號和物件。 請注意，您的 DLL 的使用者仍然需要匯入程式庫連結。  
  
 您可以使用相同的標頭檔的 DLL 和用戶端應用程式。 若要這樣做，請使用特殊的前置處理器符號，指出是否正在建立 DLL，或建置用戶端應用程式。 例如:   
  
```  
#ifdef _EXPORTING  
   #define CLASS_DECLSPEC    __declspec(dllexport)  
#else  
   #define CLASS_DECLSPEC    __declspec(dllimport)  
#endif  
  
class CLASS_DECLSPEC CExampleA : public CObject  
{ ... class definition ... };  
```  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [匯入和匯出內嵌函式](../build/importing-and-exporting-inline-functions.md)  
  
-   [交互匯入](../build/mutual-imports.md)  
  
## <a name="see-also"></a>另請參閱  
 [匯入至應用程式](../build/importing-into-an-application.md)