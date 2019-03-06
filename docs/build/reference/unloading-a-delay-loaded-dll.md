---
title: 卸載延遲載入的 DLL
ms.date: 11/04/2016
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
ms.openlocfilehash: 284a9cb9268c8c794379c6a5468b0f2b9092b7d0
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413286"
---
# <a name="unloading-a-delay-loaded-dll"></a>卸載延遲載入的 DLL

預設提供的延遲載入協助程式會檢查延遲載入描述元 pUnloadIAT 欄位中是否有指標和一份原始的匯入位址表 (IAT)。 若是如此，它會儲存在清單中，以匯入的延遲描述項的指標。 這可讓 helper 函式來尋找 DLL，支援明確卸載 DLL 的名稱。

以下是相關聯的結構和函式的明確卸載延遲載入 DLL:

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

使用 c + + 類別會實作 UnloadInfo 結構**LocalAlloc**並**LocalFree**做為其運算子的實作**新**and 運算子**刪除**分別。 這些選項會保留在使用 __puihead 做為清單的標頭的標準連結清單。

呼叫 __FUnloadDelayLoadedDLL 會嘗試尋找名稱中載入的 dll （確切的相符項目是必要的） 提供。 如果找不到，pUnloadIAT 中 IAT 的副本複製要還原的 thunk 指標執行的 IAT 之上，程式庫會釋出與**FreeLibrary**，比對**UnloadInfo**記錄已從取消連結清單和刪除，而且為 true，則會傳回。

函式 __FUnloadDelayLoadedDLL2 的引數是區分大小寫。 例如，您會指定：

```cpp
__FUnloadDelayLoadedDLL2("user32.DLL");
```

而不是：

```cpp
__FUnloadDelayLoadedDLL2("User32.DLL");.
```

## <a name="see-also"></a>另請參閱

[了解協助協助程式函式](understanding-the-helper-function.md)
