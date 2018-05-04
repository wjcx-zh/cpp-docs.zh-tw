---
title: 使用.DEF 檔匯入 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b36a68267251f76294ec6f3a0391ffa5f259704c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="importing-using-def-files"></a>使用 .DEF 檔匯入
如果您選擇使用 **__declspec （dllimport)** .def 檔，以及您應該變更.def 檔案，使用常數取代的資料來減少撰寫程式碼不正確會導致問題的可能性：  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   DATA  
```  
  
 下表顯示為何。  
  
|關鍵字|發出在匯入程式庫|匯出|  
|-------------|---------------------------------|-------------|  
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|  
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|  
  
 使用 **__declspec （dllimport)** 和常數列出兩者`imp`版本和未裝飾的名稱.lib DLL 匯入是用來允許明確連結的程式庫。 使用 **__declspec （dllimport)** 和資料清單只`imp`版本的名稱。  
  
 如果您使用常數時，下列程式碼建構可以用來存取`ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 -或-  
  
```  
ULONG *ulDataInDll;      /*prototype*/  
if (*ulDataInDll == 0L)  /*sample code fragment*/  
```  
  
 不過，如果您使用.def 檔中的資料，只有使用下列定義進行編譯的程式碼可以存取的變數`ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll;  
  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 使用常數是風險較大，因為如果您忘記使用額外的間接取值層級，您可能無法存取匯入位址表指標，此變數，不是變數本身。 因為匯入位址表目前進行唯讀的編譯器和連結器，這種問題通常可以呈現為發生存取違規。  
  
 如果看到.def 檔案中的常數來說明此情況下，目前的 Visual c + + 連結器就會發出警告。 使用常數的唯一實際原因是如果您不能重新編譯的標頭檔未列出的某些物件檔案 **__declspec （dllimport)** 原型上啟動。  
  
## <a name="see-also"></a>另請參閱  
 [匯入至應用程式](../build/importing-into-an-application.md)
