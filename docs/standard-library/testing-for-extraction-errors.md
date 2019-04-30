---
title: 測試是否有擷取錯誤
ms.date: 11/04/2016
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
ms.openlocfilehash: 62d9c94f366ec666acf2179803c62e4a3ccd7e6a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412055"
---
# <a name="testing-for-extraction-errors"></a>測試是否有擷取錯誤

[錯誤處理函式](../standard-library/output-file-stream-member-functions.md) 中所討論的輸出錯誤處理函式適用於輸入資料流。 務必測試擷取期間是否會發生錯誤。 請考量下列陳述式：

```cpp
cin>> n;
```

如果 `n` 是帶正負號的整數，則大於 32,767 (允許的最大值或 MAX_INT) 的值會設定資料流的 `fail` 位元，而 `cin` 物件會變成無法使用。 所有後續的擷取都會導致立即傳回，而且不會儲存任何值。

## <a name="see-also"></a>另請參閱

[輸入資料流](../standard-library/input-streams.md)<br/>
