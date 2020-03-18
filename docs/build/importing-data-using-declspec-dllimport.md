---
title: 使用 __declspec(dllimport) 匯入資料
ms.date: 11/04/2016
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: c9dce798572a91bcb9721f022393abb669970131
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440454"
---
# <a name="importing-data-using-__declspecdllimport"></a>使用 __declspec(dllimport) 匯入資料

在資料的情況下，使用 **__declspec （dllimport）** 是一個方便的專案，它會移除一層間接取值。 當您從 DLL 匯入資料時，您仍然必須流覽匯入位址表。 在 **__declspec （dllimport）** 之前，這表示您必須記得在存取從 DLL 匯出的資料時，執行額外的間接取值層級：

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

當您將資料標記為 **__declspec （dllimport）** 時，編譯器會自動為您產生間接取值程式碼。 您不再需要擔心上述步驟。 如先前所述，建立 DLL 時，請勿在資料上使用 **__declspec （dllimport）** 宣告。 DLL 內的函式不會使用匯入位址表來存取資料物件;因此，您將不會有額外的間接取值層級。

若要從 DLL 自動匯出資料，請使用下列宣告：

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>另請參閱

[匯入至應用程式](importing-into-an-application.md)
