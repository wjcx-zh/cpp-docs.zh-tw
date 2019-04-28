---
title: 告知攔截
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, notification hooks
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
ms.openlocfilehash: 884d8e8479b7cad28d99e19adfac4d05dbeec5f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320470"
---
# <a name="notification-hooks"></a>告知攔截

告知攔截呼叫之前在 helper 常式會執行下列動作：

- 儲存至程式庫的控制代碼會檢查是否已載入。

- **LoadLibrary**稱為嘗試載入的 dll。

- **GetProcAddress**稱為嘗試取得程序的位址。

- 返回延遲匯入負載 thunk。

已啟用通知攔截：

- 藉由提供新定義的指標 **__pfnDliNotifyHook2** ，初始化以指向您自己函式來接收通知。

   \-或-

- 藉由設定指標 **__pfnDliNotifyHook2**來攔截函式之前呼叫任何程式 DLL 延遲載入。

如果通知已**dliStartProcessing**，攔截函式可以傳回：

- NULL

   預設的協助程式會處理該 DLL 的載入。 此方法只是呼叫僅供參考之用。

- 函式指標

   略過預設延遲載入的處理。 這可讓您提供您自己的載入處理常式。

如果通知已**dliNotePreLoadLibrary**，攔截函式可以傳回：

- 0，如果只想要參考的通知。

- 載入 DLL 時，如果它載入該 DLL 本身的 HMODULE。

如果通知已**dliNotePreGetProcAddress**，攔截函式可以傳回：

- 0，如果只想要參考的通知。

- 匯入函式的位址，如果攔截函式會取得本身的位址。

如果通知已**dliNoteEndProcessing**，攔截函式的傳回值會被忽略。

如果此指標初始化 （非零），延遲載入 helper 會叫用其執行特定通知點函式。 函式指標具有下列定義：

```C
// The "notify hook" gets called for every call to the
// delay load helper.  This allows a user to hook every call and
// skip the delay load helper entirely.
//
// dliNotify == {
//  dliStartProcessing |
//  dliNotePreLoadLibrary  |
//  dliNotePreGetProc |
//  dliNoteEndProcessing}
//  on this call.
//
ExternC
PfnDliHook   __pfnDliNotifyHook2;

// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

通知傳入**DelayLoadInfo**攔截函式，以及通知值的結構。 這項資料等同於使用延遲載入 helper 常式。 通知值將會是其中一個定義中的值[結構和常數定義](structure-and-constant-definitions.md)。

## <a name="see-also"></a>另請參閱

[錯誤處理和通知](error-handling-and-notification.md)
