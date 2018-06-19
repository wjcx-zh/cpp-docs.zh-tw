---
title: 匯入資料使用 __declspec （dllimport） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9877c5a229c3cabcb7703dd2617d1d57e3512f0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368508"
---
# <a name="importing-data-using-declspecdllimport"></a>使用 __declspec(dllimport) 匯入資料
在使用資料的情況下 **__declspec （dllimport)** 是方便項目，以便移除一層間接取值。 當您從 DLL 匯入資料時，您仍然必須透過匯入位址表。 之前 **__declspec （dllimport)**，這代表您必須記得要存取資料從 DLL 匯出時執行額外的間接取值層級：  
  
```  
// project.h  
#ifdef _DLL   // If accessing the data from inside the DLL  
   ULONG ulDataInDll;  
  
#else         // If accessing the data from outside the DLL  
   ULONG *ulDataInDll;  
#endif  
```  
  
 然後會將匯出的資料中您。DEF 檔案：  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   CONSTANT  
```  
  
 而且在 DLL 外部存取：  
  
```  
if (*ulDataInDll == 0L)   
{  
   // Do stuff here  
}  
```  
  
 當您將標記資料做為 **__declspec （dllimport)**，編譯器會自動為您產生間接取值的程式碼。 您不再需要擔心上述步驟。 如先前所述，請勿使用 **__declspec （dllimport)** 宣告上的資料時建置 DLL。 函數的 DLL 中不會使用匯入位址表來存取資料的物件。因此，您必須不存在的間接取值的額外層級。  
  
 若要自動從 DLL 匯出資料，使用這個宣告：  
  
```  
__declspec(dllexport) ULONG ulDataInDLL;  
```  
  
## <a name="see-also"></a>另請參閱  
 [匯入至應用程式](../build/importing-into-an-application.md)