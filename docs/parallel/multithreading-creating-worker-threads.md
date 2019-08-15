---
title: 多執行緒：在 MFC 中建立背景工作執行緒
ms.date: 11/04/2016
helpviewer_keywords:
- multithreading [C++], worker threads
- background tasks [C++]
- threading [C++], worker threads
- worker threads [C++]
- threading [C++], creating threads
- threading [MFC], worker threads
- threading [C++], user input not required
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
ms.openlocfilehash: c8df3dd9d17819b23362a3b31d8e198883aa9143
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512059"
---
# <a name="multithreading-creating-worker-threads-in-mfc"></a>多執行緒：在 MFC 中建立背景工作執行緒

工作者執行緒通常用來處理背景工作, 使用者不應該等待繼續使用您的應用程式。 重新計算和背景列印等工作, 都是工作者執行緒的絕佳範例。 本主題詳細說明建立背景工作執行緒所需的步驟。 主題包括：

- [啟動執行緒](#_core_starting_the_thread)

- [執行控制函數](#_core_implementing_the_controlling_function)

- [範例](#_core_controlling_function_example)

建立背景工作執行緒相當簡單。 若要讓您的執行緒執行, 只需要兩個步驟: 執行控制函式和啟動執行緒。 不需要從[CWinThread](../mfc/reference/cwinthread-class.md)衍生類別。 如果您需要特殊版本的`CWinThread`, 您可以衍生類別, 但大部分簡單的背景工作執行緒都不需要。 您可以在`CWinThread`不修改的情況下使用。

##  <a name="_core_starting_the_thread"></a>啟動執行緒

有兩個多載版本`AfxBeginThread`: 一個只能建立背景工作執行緒, 另一個則可以同時建立使用者介面執行緒和背景工作執行緒。 若要使用第一個多載來開始執行您的背景工作執行緒, 請呼叫[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), 並提供下列資訊:

- 控制函式的位址。

- 要傳遞至控制函數的參數。

- 選擇性所需的執行緒優先順序。 預設值為一般優先權。 如需可用優先權層級的詳細資訊, 請參閱 Windows SDK 中的[SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 。

- 選擇性執行緒所需的堆疊大小。 預設值與建立執行緒的大小堆疊相同。

- 選擇性CREATE_SUSPENDED, 如果您想要以暫停狀態建立執行緒。 預設值為 0, 或正常啟動執行緒。

- 選擇性所需的安全性屬性。 預設值是與父執行緒相同的存取權。 如需有關此安全性資訊格式的詳細資訊, 請參閱 Windows SDK 中的[security attributes 這個](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))。

`AfxBeginThread`為您建立並`CWinThread`初始化物件, 並將其啟動並傳回其位址, 讓您稍後可以參考它。 整個程式中都會進行檢查, 以確保在建立過程中, 所有物件都已適當地解除配置。

##  <a name="_core_implementing_the_controlling_function"></a>執行控制函數

控制函數會定義執行緒。 當您輸入這個函式時, 執行緒就會啟動, 而當它結束時, 執行緒就會終止。 此函式應具有下列原型:

```
UINT MyControllingFunction( LPVOID pParam );
```

參數是單一值。 函式在此參數中接收的值是建立執行緒物件時, 傳遞至函式的值。 控制函式可以透過其選擇的任何方式來解讀此值。 它可以被視為純量值或包含多個參數之結構的指標, 也可以忽略它。 如果參數參考結構, 則結構不僅可以用來將資料從呼叫端傳遞至執行緒, 也不能用來將資料從執行緒回傳給呼叫者。 如果您使用這類結構將資料傳回給呼叫者, 則在結果準備就緒時, 執行緒必須通知呼叫者。 如需從背景工作執行緒到呼叫端通訊的詳細資訊[, 請參閱多執行緒:程式設計](multithreading-programming-tips.md)提示。

當函式終止時, 它應該會傳回指示終止原因的 UINT 值。 這個結束代碼通常是 0, 表示有其他值指出不同類型錯誤的成功。 這與純粹的執行相依。 有些執行緒可能會維護物件的使用量計數, 並傳回目前該物件的使用次數。 若要查看應用程式可以如何取得此值[, 請參閱多執行緒:終止執行緒](multithreading-terminating-threads.md)。

在以 MFC 程式庫撰寫的多執行緒程式中, 您可以執行的動作有一些限制。 如需這些限制的說明, 以及使用執行緒的其他秘訣[, 請參閱多執行緒:程式設計](multithreading-programming-tips.md)提示。

##  <a name="_core_controlling_function_example"></a>控制函數範例

下列範例顯示如何定義控制函式, 並從程式的另一個部分加以使用。

```
UINT MyThreadProc( LPVOID pParam )
{
    CMyObject* pObject = (CMyObject*)pParam;

    if (pObject == NULL ||
        !pObject->IsKindOf(RUNTIME_CLASS(CMyObject)))
    return 1;   // if pObject is not valid

    // do something with 'pObject'

    return 0;   // thread completed successfully
}

// inside a different function in the program
.
.
.
pNewObject = new CMyObject;
AfxBeginThread(MyThreadProc, pNewObject);
.
.
.
```

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [多執行緒：建立使用者介面執行緒](multithreading-creating-user-interface-threads.md)

## <a name="see-also"></a>另請參閱

[使用 C++ 和 MFC 進行多執行緒處理](multithreading-with-cpp-and-mfc.md)
