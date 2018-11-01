---
title: 'TN045: Varchar-varbinary 的 MFC 資料庫支援'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.data
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
ms.openlocfilehash: 286ef403ec4bd51b035945f3ca268b59fee4d9d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567033"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045：Long Varchar/Varbinary 的 MFC/資料庫支援

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

此附註將描述如何擷取和傳送 ODBC **SQL_LONGVARCHAR**並**SQL_LONGVARBINARY**資料型別使用 MFC 資料庫類別。

## <a name="overview-of-long-varcharvarbinary-support"></a>Long Varchar/Varbinary 支援概觀

ODBC **SQL_LONG_VARCHAR**並**SQL_LONGBINARY** （稱為這裡長資料行） 的資料類型可以保存大量的資料。 有 3 種方法，您可以處理這項資料：

- 將它繫結`CString` / `CByteArray`。

- 繫結到`CLongBinary`。

- 請勿完全將其繫結和擷取並傳送長資料值以手動的方式，獨立的資料庫類別。

每個三個方法都有其優缺點。

長資料行不支援查詢參數。 它們僅支援 outputColumns。

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>繫結至 CString/CByteArray 的長資料行

優點：

這種方法很容易理解，及您使用熟悉的類別。 「 架構 」 提供`CFormView`支援`CString`使用`DDX_Text`。 您有許多一般字串或集合的功能與`CString`和`CByteArray`類別，以及您可以控制配置在本機保存資料值的記憶體數量。 架構會維護期間的欄位資料的舊副本`Edit`或`AddNew`函式呼叫，而且架構可以自動為您偵測資料變更。

> [!NOTE]
>  由於`CString`專為處理字元資料，並`CByteArray`處理二進位資料時，建議您將字元資料 (**SQL_LONGVARCHAR**) 到`CString`，和二進位資料 (**SQL_LONGVARBINARY**) 到`CByteArray`。

RFX 函式的`CString`和`CByteArray`有其他引數，可讓您覆寫預設大小的已配置的記憶體來容納擷取的資料行的值。 請注意下列函式宣告中的 nMaxLength 引數：

```
void AFXAPI RFX_Text(CFieldExchange* pFX,
    const char *szName,
    CString& value,
    int nMaxLength = 255,
    int nColumnType =
    SQL_VARCHAR);

void AFXAPI RFX_Binary(CFieldExchange* pFX,
    const char *szName,
    CByteArray& value,
    int nMaxLength = 255);
```

如果您擷取到很長的資料行`CString`或`CByteArray`，傳回的資料量是，根據預設，255 個位元組的最大值。 除此之外的任何項目會被忽略。 在此情況下，架構會擲回例外狀況**AFX_SQL_ERROR_DATA_TRUNCATED**。 幸運的是，您可以明確地增加 nMaxLength 為更高的值，最多**MAXINT**。

> [!NOTE]
>  MFC 會使用 nMaxLength 的值來設定的本機緩衝區`SQLBindColumn`函式。 這是資料的儲存體的本機緩衝區，而且實際上不會影響的 ODBC 驅動程式所傳回的資料量。 `RFX_Text` 並`RFX_Binary`只進行一個呼叫使用`SQLFetch`從後端資料庫擷取資料。 每個 ODBC 驅動程式會有不同的限制，它們可以傳回單一擷取中的資料量。 這項限制可能會遠小於中的值設定 nMaxLength，在此情況下，例外狀況**AFX_SQL_ERROR_DATA_TRUNCATED**就會擲回。 在這些情況下，切換成使用`RFX_LongBinary`而非`RFX_Text`或`RFX_Binary`如此可以擷取所有資料。

ClassWizard 會繫結**SQL_LONGVARCHAR**要`CString`，或有**SQL_LONGVARBINARY**至`CByteArray`您。 如果您想要配置超過 255 個位元組到其中，您擷取長的資料行，您可以再提供 nMaxLength 明確的值。

當長資料行繫結至`CString`或是`CByteArray`，更新欄位的運作方式就像它繫結至時 SQL_**VARCHAR**或 SQL_**VARBINARY**。 期間`Edit`，立即和更新版本時比較快取的資料值`Update`呼叫以偵測變更的資料值和設定麻煩並適當地 Null 資料行的值。

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>繫結至 CLongBinary 的長資料行

如果您的長資料行可能包含多個**MAXINT**個位元組的資料，您應該考慮擷取到`CLongBinary`。

優點：

這樣會擷取整個很長的資料行中，最多可用的記憶體。

缺點：

資料會保留在記憶體中。 這個方法也很費不貲的非常大量的資料。 您必須呼叫`SetFieldDirty`進行繫結的資料，以確保欄位的成員會包含在`Update`作業。

如果您擷取到的長資料行`CLongBinary`，資料庫類別會檢查總大小的長資料行，則配置`HGLOBAL`夠大，無法容納它的整個資料值的記憶體區段。 資料庫類別然後擷取整個資料值到配置`HGLOBAL`。

如果資料來源無法傳回預期的長資料行大小，此架構將會擲回例外狀況**AFX_SQL_ERROR_SQL_NO_TOTAL**。 如果嘗試配置`HGLOBAL`失敗，standard 記憶體的例外狀況會擲回。

ClassWizard 會繫結**SQL_LONGVARCHAR**或是**SQL_LONGVARBINARY**到`CLongBinary`您。 選取`CLongBinary`為變數的型別，在 [加入成員變數] 對話方塊。 接著會新增 ClassWizard`RFX_LongBinary`呼叫您`DoFieldExchange`呼叫且遞增量為繫結欄位的總數。

若要更新長資料的資料行值，請先確定已配置`HGLOBAL`夠大，足以容納您的新資料，藉由呼叫 **:: GlobalSize**上*m_hData*隸屬`CLongBinary`。 如果太小，釋放`HGLOBAL`和配置一個適當的大小。 然後設定*m_dwDataLength*以反映新的大小。

否則，如果*m_dwDataLength*大小大於您要取代的資料，您可以釋放，並重新配置`HGLOBAL`，或保留配置。 請務必指出實際使用中的位元組數目*m_dwDataLength*。

## <a name="how-updating-a-clongbinary-works"></a>如何更新 CLongBinary 運作方式

您不需要了解如何更新`CLongBinary`可行，但它可能有助於範例有關如何將 long 資料值傳送至資料來源，如果您選擇這個第三個方法，如下所述。

> [!NOTE]
>  為了讓`CLongBinary`欄位包含在更新中，您必須明確呼叫`SetFieldDirty`欄位。 如果您進行任何變更至欄位，包括將它設定為 Null，您必須呼叫`SetFieldDirty`。 您還必須呼叫`SetFieldNull`，其中第二個參數是**FALSE**將標示為具有值的欄位。

更新時`CLongBinary`欄位中，資料庫類別使用 ODBC 的**DATA_AT_EXEC**機制 (請參閱 ODBC 文件`SQLSetPos`的 rgbValue 引數)。 當架構準備 insert 或 update 陳述式，而不是指向`HGLOBAL`包含資料，*地址*的`CLongBinary`已設為*值*的資料行相反地，以及長度指標設定為**SQL_DATA_AT_EXEC**。 稍後，當 update 陳述式會傳送至資料來源`SQLExecDirect`會傳回**SQL_NEED_DATA**。 這會提醒架構的參數，此資料行的值是實際的地址`CLongBinary`。 這個架構會呼叫`SQLGetData`一次使用小型緩衝區，必須是要傳回之資料的實際長度的驅動程式。 如果驅動程式會傳回二進位大型物件 (BLOB) 的實際長度，MFC 將一樣多的空間重新配置所需的擷取 BLOB。 如果資料來源會傳回**SQL_NO_TOTAL**，表示它無法判斷 BLOB 的大小，MFC 會建立較小的區塊。 預設的初始大小是 64 K 和後續的區塊都會進行倍;比方說，第二個會為 128k，第三個是 256 KB，依此類推。 初始大小是可設定的。

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>未繫結： 擷取/傳送資料直接從 ODBC 使用 SQLGetData

使用此方法，完全略過資料庫類別，並自行處理的長資料行。

優點：

您可以快取磁碟，如有必要，或決定要擷取的資料以動態方式量的資料。

缺點：

您未獲得的 framework`Edit`或`AddNew`支援，以及您必須撰寫程式碼來執行基本的功能 (`Delete`運作，因為它不是資料行層級的作業)。

在此情況下，長的資料行必須是資料錄集，選取清單中，但應該不會繫結至架構。 這是提供您自己的 SQL 陳述式，透過其中一種方式`GetDefaultSQL`或做為 lpszSQL 引數`CRecordset`的`Open`函式，並不會繫結的 RFX_ 函式呼叫的額外資料行。 ODBC 需要未繫結的欄位會顯示要繫結欄位的右邊，因此將您的繫結資料行或資料行新增至選取清單的結尾。

> [!NOTE]
>  長資料行未繫結架構，因為它的變更不會與處理`CRecordset::Update`呼叫。 您必須建立並傳送必要的 SQL**插入**並**更新**陳述式自己。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)

