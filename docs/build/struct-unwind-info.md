---
title: 結構 UNWIND_INFO |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f0aee906-a1b9-44cc-a8ad-463637bd5411
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b342aa89dd82f89b1318da3ab1acb610085a7e7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717011"
---
# <a name="struct-unwindinfo"></a>struct UNWIND_INFO

回溯資料資訊結構用來記錄函式具有堆疊指標和靜態暫存器儲存在堆疊上的效果：

|||
|-|-|
|UBYTE: 3|版本|
|UBYTE: 5|旗標|
|UBYTE|初構的大小|
|UBYTE|回溯程式碼的計數|
|UBYTE: 4|框架註冊|
|UBYTE: 4|框架註冊位移 （調整）|
|USHORT \* n|回溯程式碼陣列|
|變數|可以是表單的 （1） 或 （2） 以下版本嗎|

（1） 例外狀況處理常式

|||
|-|-|
|ULONG|例外狀況處理常式的位址|
|變數|語言特有的處理常式資料 （選擇性）|

（2） 鏈結的回溯資訊

|||
|-|-|
|ULONG|函式的起始位址|
|ULONG|函式結束位址|
|ULONG|回溯資訊位址|

UNWIND_INFO 結構必須是在記憶體中的對齊的 DWORD。 每個欄位的意義如下所示：

- **版本**

   回溯資料，目前 1 的版本號碼。

- **旗標**

   目前定義三個旗標：

   |旗標|描述|
   |-|-|
   |`UNW_FLAG_EHANDLER`| 函式有想要檢查例外狀況的函式時，應該呼叫例外狀況處理常式。|
   |`UNW_FLAG_UHANDLER`| 函式具有回溯例外狀況時，應該呼叫終止處理常式。|
   |`UNW_FLAG_CHAININFO`| 這樣的回溯資訊結構並不是主要程序。 相反地，鏈結的回溯資訊項目是先前的 RUNTIME_FUNCTION 項目的內容。 請參閱下列文字，以了解鏈結的回溯資訊結構。 如果設定此旗標，則必須先清除 UNW_FLAG_EHANDLER 和 UNW_FLAG_UHANDLER 旗標。 此外，框架登錄 」 以及 「 固定的堆疊配置欄位必須具有相同的值和主要的回溯資訊。|

- **初構的大小**

   函式初構，以位元組為單位的長度。

- **回溯程式碼的計數**

   這是在回溯程式碼陣列中的位置數目。 請注意一些回溯程式碼 (例如 UWOP_SAVE_NONVOL) 需要在陣列中的多個位置。

- **框架註冊**

   如果是非零值，然後此函數會使用框架指標，且此欄位做為框架指標，使用相同的編碼方式和 UNWIND_CODE 節點的 [作業資訊] 欄位之靜態暫存器的數目。

- **框架註冊 （調整） 的位移**

   如果框架註冊欄位為非零值，這是從它建立時套用至 fp RSP 縮放的位移。 在實際的 fp 設 RSP + 16\*這個數字，允許從 0 到 240 的位移。 這可讓指向 fp 動態堆疊框架，允許更好的程式碼密度，透過較短的指令 （詳細指示可以使用 8 位元帶正負號位移的形式） 的本機堆疊配置的中間。

- **回溯程式碼陣列**

   這是靜態暫存器和 RSP 說明效果的初構項目的陣列。 請參閱區段和 UNWIND_CODE 相關的個別項目的意義。 用於對齊用途，此陣列一定會偶數數目的項目，可能未使用的最後一個項目 （在此情況下則陣列將會超過計數的回溯程式碼欄位所指出的其中一個）。

- **例外狀況處理常式的位址**

   （如果 UNW_FLAG_CHAININFO 的旗標已清除，而且已設定其中一個 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER 的旗標），這是其中一個函式的特定語言的例外狀況/終止處理常式的相對映像的指標。

- **語言特有的處理常式的資料**

   這是函式的語言特定的例外狀況處理常式的資料。 這些資料的格式是未指定，並完全取決於使用中的特定例外狀況處理常式。

- **鏈結的回溯資訊**

   如果設定旗標 UNW_FLAG_CHAININFO UNWIND_INFO 結構結尾三個 UWORDs。  這些 UWORDs 代表函式的鏈結的回溯 RUNTIME_FUNCTION 的資訊。

## <a name="see-also"></a>另請參閱

[回溯資料以進行例外狀況處理與偵錯工具支援](../build/unwind-data-for-exception-handling-debugger-support.md)