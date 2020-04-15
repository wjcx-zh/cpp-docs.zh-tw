---
title: Visual C++ 6.0 之後 DLL 延遲載入 Helper 函式的變更
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
ms.openlocfilehash: 536729e27c89d068957ea451355957e4a35348ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320615"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Visual C++ 6.0 之後 DLL 延遲載入 Helper 函式的變更

如果電腦上有多個版本的 Visual C++,或者如果您定義了自己的幫助程式功能,則可能會受到對 DLL 延遲載入説明程式功能所做的更改的影響。 例如：

- **__delayLoadHelper**現在 **__delayLoadHelper2**

- **__pfnDliNotifyHook**現在 **__pfnDliNotifyHook2**

- **__pfnDliFailureHook**正在 **__pfnDliFailureHook2**

- **__FUnloadDelayLoadedDLL**現在 **__FUnloadDelayLoadedDLL2**

> [!NOTE]
> 如果使用默認幫助器函數,這些更改不會影響您。 對於調用連結器的方式,沒有更改。

## <a name="multiple-versions-of-visual-c"></a>視覺化C++的多個版本

如果電腦上有多個版本的 Visual C++,請確保連結器與 delayimp.lib 匹配。 如果不匹配,您將獲得連結器錯誤報告或`___delayLoadHelper2@8``___delayLoadHelper@8`作為未解析的外部符號。 前者意味著一個新的連結器與舊的delayimp.lib,後者意味著一個舊連結器與一個新的delayimp.lib。

如果收到未解析的連結器錯誤,則在 delayimp.lib 上運行[轉儲bin/linker成員](linkermember.md):1,您希望該函數包含説明器函數,以查看定義哪個説明器函數。 説明器函數也可以在物件檔中定義;也可以在物件檔中定義説明器函數。執行[傾印 bin /符號](symbols.md)並尋找`delayLoadHelper(2)`。

如果您知道您具有 Visual C++ 6.0 連結器,則:

- 在延遲載入說明器的 .lib 或 .obj 檔執行轉印bin,以確定它是否定義 **__delayLoadHelper2**。 如果沒有,連結將失敗。

- 在延遲載入幫助器的 .lib 或 .obj 檔中定義 **__delayLoadHelper。**

## <a name="user-defined-helper-function"></a>使用者定義的說明器功能

如果您定義了自己的說明器功能並使用目前版本的 Visual C++,請執行以下操作:

- 將說明器函數重新命名為 **__delayLoadHelper2**。

- 由於延遲描述符中的指標(delayimp.h 中的 ImgDelayDescr)已經從絕對位址 (VA) 更改為相對位址 (RVA),在 32 位元和 64 位元程序中按預期方式工作,因此您需要將這些指標轉換回指標。 引入了一項新功能:PFromRva,在 delayhlp.cpp中發現。 可以在描述符中的每個欄位上使用此函數將它們轉換回 32 位元或 64 位元指標。 默認延遲載入幫助器函數仍然是一個很好的範本,用作範例。

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>載入延遲載入 DLL 的所有匯入

連結器可以從指定的延遲載入 DLL 載入所有導入。 有關詳細資訊[,請參閱載所有匯入以瞭解延遲載入 DLL。](loading-all-imports-for-a-delay-loaded-dll.md)

## <a name="see-also"></a>另請參閱

[了解協助協助程式函式](understanding-the-helper-function.md)
