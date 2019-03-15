---
title: 使用 __declspec(dllimport) 匯入資料
ms.date: 11/04/2016
f1_keywords:
- dllimport
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: 74ad93e640a4e961f7670077227bb5c35a42c20f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818423"
---
# <a name="importing-data-using-declspecdllimport"></a>使用 __declspec(dllimport) 匯入資料

在使用資料的情況下 **__declspec （dllimport)** 是移除一層間接取值的便利性項目。 當您匯入資料，從 DLL 時，您仍然必須通過 匯入位址表格。 再 **__declspec （dllimport)**，這表示您必須記得先執行另一層間接取值時存取的資料從 DLL 匯出：

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

然後匯出的資料，在您。DEF 檔案：

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

及存取外部 DLL:

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

當您將標記資料作為 **__declspec （dllimport)**，編譯器會自動為您產生的間接取值的程式碼。 您不再需要擔心上述步驟。 如先前所述，不用 **__declspec （dllimport)** 建置 DLL 時對資料的宣告。 DLL 內的函式來存取資料的物件; 請勿匯入位址表格因此，您將沒有額外的層級的間接取值的存在。

若要自動從 DLL 匯出資料，使用這個宣告：

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>另請參閱

[匯入至應用程式](importing-into-an-application.md)
