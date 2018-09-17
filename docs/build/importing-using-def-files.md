---
title: 使用 DEF 檔匯入 |Microsoft Docs
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
ms.openlocfilehash: 3e1562e14b20e4e1dd96764414978889d6205179
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710537"
---
# <a name="importing-using-def-files"></a>使用 .DEF 檔匯入

如果您選擇使用 **__declspec （dllimport)** .def 檔，以及您應該變更.def 檔，使用常數取代的資料來降低，正確撰寫程式碼將會導致問題的可能性：

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

下表顯示原因。

|關鍵字|發出在匯入程式庫|匯出|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

使用 **__declspec （dllimport)** 常數列出兩者`imp`版本和未裝飾的名稱.lib DLL 匯入已建立，以允許明確連結的程式庫。 使用 **__declspec （dllimport)** 和資料清單只`imp`版本的名稱。

如果您使用常數時，下列程式碼建構其中一種方法可以用來存取`ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\-或-

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

不過，如果您使用.def 檔案中的資料，只編譯使用下列定義的程式碼可以存取該變數`ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

使用常數是風險較大，因為如果您忘記使用額外間接取值層，您可能會存取匯入位址表格的指標，此變數，不是變數本身。 因為匯入位址表格目前做唯讀的編譯器和連結器，則這種問題通常可以呈現為存取違規。

如果發現.def 檔案中的常數，帳戶在此情況下，目前的 Visual c + + 連結器會發出警告。 若要使用常數唯一真正的原因是如果您無法重新編譯的標頭檔未列出一些物件檔案 **__declspec （dllimport)** 原型上啟動。

## <a name="see-also"></a>另請參閱

[匯入至應用程式](../build/importing-into-an-application.md)
