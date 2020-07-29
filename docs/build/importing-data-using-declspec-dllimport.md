---
title: 使用 __declspec(dllimport) 匯入資料
ms.date: 11/04/2016
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: 341912b53301c3a11df4285167d66c8c1493d2fd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223989"
---
# <a name="importing-data-using-__declspecdllimport"></a>使用 __declspec(dllimport) 匯入資料

在資料的案例中，使用 **`__declspec(dllimport)`** 是移除間接取值層的便利專案。 當您從 DLL 匯入資料時，您仍然必須流覽匯入位址表。 在 **`__declspec(dllimport)`** 此之前，這意味著您必須記得在存取從 DLL 匯出的資料時，執行額外的間接取值層級：

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

接著，您會匯出中的資料。DEF 檔案：

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

並在 DLL 外部存取它：

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

當您將資料標記為時 **`__declspec(dllimport)`** ，編譯器會自動為您產生間接取值程式碼。 您不再需要擔心上述步驟。 如先前所述， **`__declspec(dllimport)`** 建立 DLL 時，請勿在資料上使用宣告。 DLL 內的函式不會使用匯入位址表來存取資料物件;因此，您將不會有額外的間接取值層級。

若要從 DLL 自動匯出資料，請使用下列宣告：

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>另請參閱

[匯入至應用程式](importing-into-an-application.md)
