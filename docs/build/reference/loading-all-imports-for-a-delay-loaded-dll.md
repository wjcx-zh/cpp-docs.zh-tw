---
title: 載入延遲載入 DLL 的所有匯入
ms.date: 11/04/2016
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
ms.openlocfilehash: a9e9df6b0bae49eaf599e56e5d96040afae315e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536561"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>載入延遲載入 DLL 的所有匯入

**__HrLoadAllImportsForDll**函式，其定義於 delayhlp.cpp，會告訴連結器，以從已經使用指定的 DLL 載入所有匯入[/delayload](../../build/reference/delayload-delay-load-import.md)連結器選項。

載入所有匯入，可讓您放在程式碼中的一個位置中的錯誤處理，並不一定要使用的匯入實際的呼叫周圍處理的例外狀況。 它也可避免透過載入匯入失敗的協助程式程式碼處理部分失敗應用程式的情況。

呼叫 **__HrLoadAllImportsForDll**不會變更行為的攔截程序和錯誤處理; 請參閱[錯誤處理和通知](../../build/reference/error-handling-and-notification.md)如需詳細資訊。

DLL 名稱傳遞給 **__HrLoadAllImportsForDll**比較儲存在 DLL 本身的名稱，且區分大小寫。

下列範例示範如何呼叫 **__HrLoadAllImportsForDll**:

```
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>另請參閱

[延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)