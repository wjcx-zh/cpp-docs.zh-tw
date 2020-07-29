---
title: 卸載延遲載入的 DLL
ms.date: 11/04/2016
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
ms.openlocfilehash: 1895bf12cb195ef7b4555d400badf112d377547b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211914"
---
# <a name="unloading-a-delay-loaded-dll"></a>卸載延遲載入的 DLL

預設提供的延遲載入協助程式會檢查延遲載入描述項是否有指標，以及 pUnloadIAT 欄位中原始匯入位址表（IAT）的複本。 若是如此，它會將清單中的指標儲存至匯入延遲描述項。 這可讓 helper 函式依名稱尋找 DLL，以支援明確卸載該 DLL。

以下是明確卸載延遲載入 DLL 的相關聯結構和函式：

```cpp
//
// Unload support from delayimp.h
//

// routine definition; takes a pointer to a name to unload

ExternC
BOOL WINAPI
__FUnloadDelayLoadedDLL2(LPCSTR szDll);

// structure definitions for the list of unload records
typedef struct UnloadInfo * PUnloadInfo;
typedef struct UnloadInfo {
    PUnloadInfo     puiNext;
    PCImgDelayDescr pidd;
    } UnloadInfo;

// from delayhlp.cpp
// the default delay load helper places the unloadinfo records in the
// list headed by the following pointer.
ExternC
PUnloadInfo __puiHead;
```

UnloadInfo 結構是使用 c + + 類別來執行，其會使用**LocalAlloc**和**LocalFree**實作為其運算子 **`new`** 和運算子 **`delete`** 。 這些選項會使用 __puiHead 做為清單的標頭，保留在標準連結清單中。

呼叫 __FUnloadDelayLoadedDLL 將會嘗試尋找您在載入的 Dll 清單中提供的名稱（需要完全相符）。 如果找到，pUnloadIAT 中的 IAT 複本就會複製到執行的 IAT 頂端，以還原 Thunk 指標、使用**FreeLibrary**釋放程式庫、將相符的**UnloadInfo**記錄從清單中取消連結並加以刪除，然後傳回 TRUE。

函數 __FUnloadDelayLoadedDLL2 的引數會區分大小寫。 例如，您可以指定：

```cpp
__FUnloadDelayLoadedDLL2("user32.DLL");
```

而不是：

```cpp
__FUnloadDelayLoadedDLL2("User32.DLL");.
```

## <a name="see-also"></a>另請參閱

[瞭解 Helper 函式](understanding-the-helper-function.md)
