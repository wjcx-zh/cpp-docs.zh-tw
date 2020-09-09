---
title: 使用 __declspec(dllimport) 匯入資料
description: 如何使用 __declspec (dllimport) 匯入 DLL 資料。
ms.date: 09/03/2020
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: cb9850306d6e73b88e2926a6f068ae21f8d32530
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609121"
---
# <a name="importing-data-using-__declspecdllimport"></a>使用匯入資料 `__declspec(dllimport)`

在資料的案例中，使用 **`__declspec(dllimport)`** 是移除間接取值層的便利專案。 當您從 DLL 匯入資料時，您仍然必須經過匯入位址表。 在 **`__declspec(dllimport)`** 此之前，這表示您必須記得在存取從 DLL 匯出的資料時，執行額外的間接取值層級：

```C
// project.h
// Define PROJECT_EXPORTS when building your DLL
#ifdef PROJECT_EXPORTS   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

然後，您會匯出中的資料。DEF 檔案：

```DEF
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

並在 DLL 外部存取它：

```C
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

當您將資料標示為時 **`__declspec(dllimport)`** ，編譯器會自動為您產生間接程式碼。 您不再需要擔心上述步驟。 如先前所述， **`__declspec(dllimport)`** 建立 DLL 時，請勿對資料使用宣告。 DLL 內的函數不會使用匯入位址表來存取資料物件;因此，您不會有額外的間接取值層級。

若要從 DLL 自動匯出資料，請使用下列宣告：

```C
// project.h
// Define PROJECT_EXPORTS when building your DLL
#ifdef PROJECT_EXPORTS   // If accessing the data from inside the DLL
   __declspec(dllexport) ULONG ulDataInDLL;

#else         // If accessing the data from outside the DLL
   __declspec(dllimport) ULONG ulDataInDLL;
#endif
```

## <a name="see-also"></a>另請參閱

[匯入至應用程式](importing-into-an-application.md)
