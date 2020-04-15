---
title: TN045：Long Varchar-Varbinary 的 MFC-資料庫支援
ms.date: 11/04/2016
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
ms.openlocfilehash: f67d159fb600dcacd8eedd40e672edf18bddee9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365502"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045：Long Varchar/Varbinary 的 MFC/資料庫支援

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本說明介紹如何使用 MFC 資料庫類檢索和發送 ODBC **SQL_LONGVARCHAR**和**SQL_LONGVARBINARY**數據類型。

## <a name="overview-of-long-varcharvarbinary-support"></a>長瓦爾查爾/瓦二進位支援概述

ODBC **SQL_LONG_VARCHAR**和**SQL_LONGBINARY**資料類型(此處稱為長數據列)可以保存大量數據。 有三種方法可以處理這些資料:

- 繫結到`CString`/`CByteArray`。

- 繫結到`CLongBinary`。

- 完全不要綁定它,並手動檢索和發送長數據值,與資料庫類無關。

這三種方法各有優缺點。

查詢的參數不支援長數據列。 它們僅支援輸出列。

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>將長資料列繫結到 CString/CByteArray

優點：

此方法易於理解,並且您使用熟悉的類。 該框架為`CFormView``CString`提供了`DDX_Text`對的支援。 您具有大量常規字串或集合功能`CString`和`CByteArray`類,您可以控制在本地分配的記憶體量以儲存資料值。 框架在或`Edit``AddNew`函數調用期間維護欄位數據的舊副本,並且框架可以自動檢測對數據的更改。

> [!NOTE]
> 由於`CString`用於處理字元`CByteArray`數據,以及處理二進位資料,因此建議您將字元資料 **(SQL_LONGVARCHAR**`CString`) 放入中,並將二進位資料 **(SQL_LONGVARBINARY)** 放入`CByteArray`中。

RFX 函`CString`數`CByteArray`,並且 具有一個附加參數,允許您覆蓋已分配記憶體的預設大小,以保存數據列的檢索值。 請注意以下函數聲明中的 nMaxLength 參數:

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

如果將長數據列檢索到`CString``CByteArray`或 中,默認情況下,返回的最大數據量為 255 位元組。 除此以外的任何內容都將被忽略。 在這種情況下,框架將AFX_SQL_ERROR_DATA_TRUNCATED**引發異常。** 幸運的是,您可以顯式將 nMaxLength 增加到更大的值,最高為**MAXINT**。

> [!NOTE]
> MFC 使用 nMaxLength 的`SQLBindColumn`值來設置 函數的本地緩衝區。 這是用於存儲數據的本地緩衝區,實際上不會影響ODBC驅動程式返回的數據量。 `RFX_Text`並`RFX_Binary`進行一次調用`SQLFetch`,用於從後端資料庫檢索數據。 每個 ODBC 驅動程式對可在單個提取中返回的數據量有不同的限制。 此限制可能比 nMaxLength 中設置的值小得多,在這種情況下,將引發**異常AFX_SQL_ERROR_DATA_TRUNCATED。** 在這些情況下,切換到使用`RFX_LongBinary``RFX_Text`而不是`RFX_Binary`或這樣,以便檢索所有數據。

ClassWizard 會將**SQL_LONGVARCHAR**`CString`綁定到 ,或`CByteArray`將**SQL_LONGVARBINARY**綁定 到 如果要將超過 255 個字節分配給檢索長數據列,則可以為 nMaxLength 提供顯式值。

當長數據列綁定`CString`到`CByteArray`或 時,更新欄位的工作方式與綁定到SQL_**VARCHAR**或SQL_**VARBINARY**時的工作方式相同。 在`Edit`期間,數據值將緩存離開,並在調用時`Update`進行比較,以檢測對數據值的更改並適當地設置列的「臟」和「空」值。

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>將長資料列繫結到 CLongBinary

如果長資料列可能包含更多**MAXINT**位元組的資料,則可能需要考慮將其`CLongBinary`檢索到中 。

優點：

這將檢索整個長數據列,最多可訪問記憶體。

缺點：

數據存儲在記憶體中。 對於大量數據來說,這種方法的成本也高得令人望而卻步。 您必須調用`SetFieldDirty`綁定的數據成員,以確保該欄位包含`Update`在操作中。

如果將長數據列檢索到`CLongBinary`中 ,資料庫類將檢查長數據列的總大小,然後分配足夠`HGLOBAL`大的 記憶體段以容納整個數據值。 然後,資料庫類將整個數據值檢索到分配的`HGLOBAL`中。

如果數據源無法返回長數據列的預期大小,則框架將AFX_SQL_ERROR_SQL_NO_TOTAL**引發異常。** 如果嘗試分配`HGLOBAL`失敗 ,將引發標準記憶體異常。

ClassWizard`CLongBinary`會為您綁定**SQL_LONGVARCHAR**或**SQL_LONGVARBINARY。** 在`CLongBinary`「添加成員變數」對話框中選擇"變數類型」。 然後,ClassWizard`RFX_LongBinary`將呼叫添加到`DoFieldExchange`您的話務,並增加綁定欄位的總數。

`HGLOBAL`要更新長資料列值,首先通過在`CLongBinary`m_hData 成員上調用 **:: GlobalSize,** 確保已分配*m_hData*的值足夠大以 保存新數據。 如果太小,釋放`HGLOBAL`並分配一個適當的大小。 然後設置*m_dwDataLength*以反映新大小。

否則,如果*m_dwDataLength*大於要替換的數據的大小,則可以釋放並重新分配`HGLOBAL`, 也可以將其保留為分配。 請確保指示*m_dwDataLength*中實際使用的位元組數。

## <a name="how-updating-a-clongbinary-works"></a>更新 CLongBinary 的工作原理

不必瞭解更新`CLongBinary`如何工作,但如果選擇下面介紹的第三種方法,則瞭解如何向數據源發送長數據值的示例可能很有用。

> [!NOTE]
> 為了在更新中`CLongBinary`包含欄位,必須顯式調`SetFieldDirty`用 該欄位。 如果對欄位進行任何變更(包括將其設定為 Null),則必須呼`SetFieldDirty`叫 。 您必須呼叫`SetFieldNull`,第二個參數為**FALSE,** 以將欄位標記為具有值。

更新`CLongBinary`欄位時,資料庫類使用 ODBC**的DATA_AT_EXEC**機制(請`SQLSetPos`參閱有關 rgbValue 參數的 ODBC 文件)。 當框架準備插入或更新敘述時,`HGLOBAL`而不是指向包含資料,而是將的*address*`CLongBinary`位址設定為欄*的值*,長度指示器設定為**SQL_DATA_AT_EXEC**。 稍後,當更新敘述傳送到資料來源時`SQLExecDirect`, 傳回**SQL_NEED_DATA**。 這會提醒框架,此欄的參數值是的位址`CLongBinary`。 框架使用小`SQLGetData`緩衝區調用一次,期望驅動程式返回數據的實際長度。 如果驅動程式返回二進位大型物件(BLOB)的實際長度,MFC將重新分配獲取 BLOB 所需的空間。 如果數據源返回**SQL_NO_TOTAL**,指示它無法確定 BLOB 的大小,則 MFC 將創建較小的塊。 默認初始大小為 64K,後續塊的大小將是兩倍;例如,第二個將是 128K,第三個是 256K,等等。 初始大小是可配置的。

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>不結合:使用 SQLGetData 直接從 ODBC 檢索/傳送資料

使用此方法,您可以完全繞過資料庫類,並自行處理長數據列。

優點：

如有必要,可以將數據緩存到磁碟,也可以動態決定要檢索的數據量。

缺點：

您沒有得到框架`Edit``AddNew`或 支援,您必須自己編寫代碼以執行基本`Delete`功能( 雖然確實工作,因為它不是列級操作)。

在這種情況下,長數據列必須位於記錄集的選擇清單中,但不應受框架的約束。 這樣做的一種方法是通過`GetDefaultSQL`或作為 lpszSQL 參數`CRecordset``Open`提供您自己的 SQL 語句,而不是將附加列與RFX_函數調用綁定。 ODBC 要求未綁定欄位顯示在綁定欄位的右側,因此將未綁定列或列添加到選擇清單的末尾。

> [!NOTE]
> 由於長數據列不受框架的約束,因此不會通過`CRecordset::Update`調用處理對它的更改。 您必須自己建立併發送所需的 SQL **INSERT**和**更新**語句。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
