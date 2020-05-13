---
title: 建立 CArchive 物件的兩種方式
ms.date: 11/04/2016
helpviewer_keywords:
- CArchive class [MFC], closing CArchive objects
- CArchive objects [MFC], closing
- I/O [MFC], creating CArchive objects
- serialization [MFC], CArchive class
- CArchive objects [MFC]
- storage [MFC], CArchive class [MFC]
- data storage [MFC], CArchive class
- CArchive class [MFC], constructor
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
ms.openlocfilehash: 71592584d4ecdd3169ad894861a97fa668c04ee8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370950"
---
# <a name="two-ways-to-create-a-carchive-object"></a>建立 CArchive 物件的兩種方式

建立 `CArchive` 物件的方法有兩種：

- [以框架隱式建立 CArchive 物件](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [明確建立 CArchive 物件](#_core_explicit_creation_of_a_carchive_object)

## <a name="implicit-creation-of-a-carchive-object-via-the-framework"></a><a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>以框架隱式建立 CArchive 物件

最常見和最簡單的方法是讓框架代表「檔」功能表上的「儲存`CArchive`」、「儲存為」和「打開」命令為文檔創建物件。

下面是當應用程式的使用者從「檔」選單中發出「儲存為」命令時,框架的作用:

1. 顯示「**另存為」** 對話方塊並從使用者獲取檔名。

1. 開啟使用者命名的`CFile`物件檔。

1. 建立指向`CArchive``CFile`此物件的物件。 在創建物件`CArchive`時,框架將模式設置為"存儲"(寫入、序列化),而不是"載入"(讀取、反序列化)。

1. 調用派生`Serialize`類`CDocument`中 定義的函數,將其`CArchive`傳遞給 物件的引用。

然後,文檔的`Serialize`功能 將數據`CArchive`寫入 物件,如稍後所述。 從函數`Serialize`返回后,框架將銷`CArchive`毀 物件,然後`CFile`銷毀 該物件。

因此,如果讓框架為文檔`CArchive`創建 物件,則所有要做的就是實現`Serialize`文檔的 函數,該函數在存檔中寫入和讀取。 您還必須`Serialize`實現`CObject``Serialize`文檔 函數反過來直接或間接序列化的任何派生物件。

## <a name="explicit-creation-of-a-carchive-object"></a><a name="_core_explicit_creation_of_a_carchive_object"></a>明確建立 CArchive 物件

除了通過框架序列化文檔外,還有其他可能`CArchive`需要 對象的情況。 例如,您可能希望序列化數據,並從剪貼簿(由`CSharedFile`物件表示)進行序列化。 或者,您可能希望使用使用者介面儲存與框架提供的檔案不同的檔案。 在這種情況下,您可以顯示式建立物件`CArchive`。 使用以下過程,使用框架相同的方式執行此操作。

#### <a name="to-explicitly-create-a-carchive-object"></a>明確建立 CArchive 物件

1. 構造派生`CFile``CFile`自的物件或物件。

1. 將`CFile`物件傳遞給`CArchive`的 建構函數,如以下範例所示:

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   `CArchive`建構函數的第二個參數是枚舉值,該值指定存檔是否將用於存儲或載入資料到檔或從檔中載入資料。 物件的`Serialize`函數通過調用存檔物件`IsStoring`的 函數來檢查此狀態。

完成儲存或載入資料到或從物件載入後,`CArchive`關閉它。 儘管`CArchive`(`CFile`和 ) 物件將自動關閉存檔(和檔),但最好顯式關閉存檔(和檔),因為它使從錯誤中恢復更容易。 有關錯誤處理的詳細資訊,請參閱文章[「例外:捕獲和刪除異常](../mfc/exceptions-catching-and-deleting-exceptions.md)」。

#### <a name="to-close-the-carchive-object"></a>關閉 CArchive 物件

1. 下面的範例說明如何關閉`CArchive`物件:

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>另請參閱

[序列化：序列化物件](../mfc/serialization-serializing-an-object.md)
