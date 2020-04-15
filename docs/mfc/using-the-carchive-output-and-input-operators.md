---
title: 使用 CArchive&lt;&lt;&gt;&gt;與運算子
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 91ea565867cc0cb3b27ad9d5597037b637cb6544
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368967"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>使用 CArchive&lt;&lt;&gt;&gt;與運算子

`CArchive`提供<\<和 >> 運算符,用於編寫和讀取簡單的數據類型以及`CObject`從檔進行和讀取。

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>使用歸檔儲存在檔案中

1. 下面的範例簡報如何透過存檔將物件儲存在檔案中:

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>從以前儲存在檔案中的值載入物件

1. 下面的範例展示如何從以前儲存在檔案中的值載入物件:

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

通常,在派生類`Serialize``CObject`的 函數中,通過存檔存儲和載入數據,並且必須使用DECLARE_SERIALIZE宏聲明。 對`CArchive`物件的參考傳送給`Serialize`函數 。 呼叫`IsLoading``CArchive`物件的函數以確定是否已呼`Serialize`叫 函數以將資料從檔載入或將資料儲存到檔案中。

可`Serialize``CObject`序列化派生類的函數通常具有以下形式:

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

上述代碼範本與 AppWizard`Serialize`為文檔的函數(`CDocument`派生自的類)創建的一個代碼範本完全相同。 此代碼樣本可説明您編寫更易於查看的代碼,因為儲存代碼和載入代碼應始終並行,如以下範例所示:

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

函式庫**<** 將**>>** 第`CArchive`一個操作數和運算元定義為第一個操作數,以下資料類型和類別型態定義為第二個操作數:

||||
|-|-|-|
|`CObject*`|**尺寸**與`CSize`|**浮動**|
|**WORD**|`CString`|**點**和`CPoint`|
|`DWORD`|**位元組**|`RECT` 和 `CRect`|
|**雙**|**長**|`CTime` 和 `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
> 通過存檔存儲`CObject`和載入 s 需要額外考慮。 有關詳細資訊,請參閱[通過存檔存儲和載入 CObjects。](../mfc/storing-and-loading-cobjects-via-an-archive.md)

**CArchive<\<****>>** 和 運算元始終返回`CArchive`對 物件的引用,這是第一個操作數。 這使您能夠連結運算符,如下圖所示:

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>另請參閱

[序列化：序列化物件](../mfc/serialization-serializing-an-object.md)
