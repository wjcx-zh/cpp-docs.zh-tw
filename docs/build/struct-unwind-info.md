---
title: 結構 UNWIND_INFO |Microsoft 文件
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
ms.openlocfilehash: 14b17a79905ffc7814e2aecf92e90f3db526453f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383237"
---
# <a name="struct-unwindinfo"></a>struct UNWIND_INFO
回溯資料資訊結構用來記錄的影響函式的堆疊指標和靜態暫存器儲存在堆疊上的位置：  
  
|||  
|-|-|  
|UBYTE: 3|版本|  
|UBYTE: 5|旗標|  
|UBYTE|初構的大小|  
|UBYTE|回溯程式碼的計數|  
|UBYTE: 4|框架暫存器|  
|UBYTE: 4|框架暫存器位移 （縮放）|  
|USHORT * n|回溯程式碼陣列|  
|變數|可以是表單的 （1） 或 （2） 以下版本嗎|  
  
 （1） 例外狀況處理常式  
  
|||  
|-|-|  
|ULONG|例外狀況處理常式的位址|  
|變數|將語言特定處理常式資料 （選擇性）|  
  
 （2） 鏈結的回溯資訊  
  
|||  
|-|-|  
|ULONG|函式的起始位址|  
|ULONG|函式結束位址|  
|ULONG|回溯資訊位址|  
  
 UNWIND_INFO 結構必須是 DWORD 在記憶體中的對齊。 每個欄位的意義如下所示：  
  
 **版本**  
 回溯資料，目前 1 的版本號碼。  
  
 **旗標**  
 目前未定義三個旗標：  
  
 UNW_FLAG_EHANDLER 函式會有例外狀況處理常式應該尋找需要檢查例外狀況的函式時呼叫。  
  
 UNW_FLAG_UHANDLER 函式具有回溯例外狀況時，應該呼叫終止處理常式。  
  
 UNW_FLAG_CHAININFO 這回溯資訊結構不是主要的程序。 相反地，鏈結回溯項目就是先前 RUNTIME_FUNCTION 項目內容的資訊。 下列文字的說明，請參閱 < 鏈結的回溯資訊結構。 如果設定此旗標，則必須清除 UNW_FLAG_EHANDLER 和 UNW_FLAG_UHANDLER 旗標。 此外，這些框架登錄 」 以及 「 固定的堆疊配置欄位必須擁有相同的值如同主要回溯資訊。  
  
 **初構的大小**  
 函式初構以位元組為單位的長度。  
  
 **回溯程式碼的計數**  
 這是回溯程式碼陣列中的位置數目。 請注意一些回溯程式碼 (例如，UWOP_SAVE_NONVOL) 需要在陣列中的多個位置。  
  
 **框架暫存器**  
 如果是非零值，此函數會使用框架指標，然後，此欄位會用作框架指標，使用相同的編碼方式和 UNWIND_CODE 節點的操作資訊欄位之靜態暫存器的數目。  
  
 **框架註冊位移 （縮放）**  
 如果框架暫存器欄位不是零，這是從建立時，會套用至 fp 的 RSP 縮放的位移。 實際的 fp 設 RSP + 16 * 這個數字，允許從 0 到 240 的位移。 這允許 fp 指向動態堆疊框架，更好的程式碼密度，透過較短的指示 （詳細指示可以使用 8 位元帶正負號位移的形式） 的本機堆疊配置的中間。  
  
 **回溯程式碼陣列**  
 這是靜態暫存器和 RSP 說明的初構影響的項目陣列。 請參閱和 UNWIND_CODE 上的個別項目的意義。 為了對齊時，這個陣列一定會為偶數的項目，可能未使用的最後一個項目 （在此情況下陣列會是其中一個時間超過指定的回溯程式碼欄位計數）。  
  
 **例外狀況處理常式的位址**  
 （如果旗標 UNW_FLAG_CHAININFO 已清除且已設定其中一個 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER 的旗標），這是其中一個函式的特定語言的例外狀況/終止處理常式的映像的相對指標。  
  
 **將語言特定處理常式資料**  
 這是函式的語言特定的例外狀況處理常式的資料。 這項資料的格式是未指定，並完全取決於使用中的特定例外狀況處理常式。  
  
 **鏈結的回溯資訊**  
 如果在設定旗標 UNW_FLAG_CHAININFO UNWIND_INFO 結構結尾三個 UWORDs。  這些 UWORDs 代表 RUNTIME_FUNCTION 的資訊函式的鏈結的回溯。  
  
## <a name="see-also"></a>另請參閱  
 [回溯資料以進行例外狀況處理與偵錯工具支援](../build/unwind-data-for-exception-handling-debugger-support.md)