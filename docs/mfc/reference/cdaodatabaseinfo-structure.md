---
title: CDaoDatabaseInfo 結構
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabaseInfo
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
ms.openlocfilehash: 60972aa3ecaef4d38c9a0d0ecc70477796aa37aa
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304260"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo 結構

`CDaoDatabaseInfo` 結構包含針對資料存取物件（DAO）定義之資料庫物件的相關資訊。 DAO 3.6 是最後的版本，被視為已淘汰。

## <a name="syntax"></a>語法

```
struct CDaoDatabaseInfo
{
    CString m_strName;       // Primary
    BOOL m_bUpdatable;       // Primary
    BOOL m_bTransactions;    // Primary
    CString m_strVersion;    // Secondary
    long m_lCollatingOrder;  // Secondary
    short m_nQueryTimeout;   // Secondary
    CString m_strConnect;    // All
};
```

#### <a name="parameters"></a>參數

*m_strName*<br/>
唯一命名資料庫物件。 若要直接取得這個屬性，請呼叫[CDaoDatabase：： GetName](../../mfc/reference/cdaodatabase-class.md#getname)。 如需詳細資訊，請參閱 DAO 說明中的「名稱屬性」主題。

*m_bUpdatable*<br/>
指出是否可以對資料庫進行變更。 若要直接取得這個屬性，請呼叫[CDaoDatabase：： CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate)。 如需詳細資訊，請參閱 DAO 說明中的「可更新屬性」主題。

*m_bTransactions*<br/>
指出資料來源是否支援交易，這是一系列變更的記錄，稍後可以復原（取消）或認可（儲存）。 如果資料庫是以 Microsoft Jet 資料庫引擎為基礎，交易屬性為非零，而且您可以使用交易。 其他資料庫引擎可能不支援交易。 若要直接取得這個屬性，請呼叫[CDaoDatabase：： CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact)。 如需詳細資訊，請參閱 DAO 說明中的「交易屬性」主題。

*m_strVersion*<br/>
指出 Microsoft Jet 資料庫引擎的版本。 若要直接取得這個屬性的值，請呼叫資料庫物件的[GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion)成員函式。 如需詳細資訊，請參閱 DAO 說明中的「版本屬性」主題。

*m_lCollatingOrder*<br/>
指定文字中的排序次序順序，以進行字串比較或排序。 可能的值包括：

- `dbSortGeneral` 使用一般（英文、法文、德文、葡萄牙文、義大利文和新式西班牙文）排序次序。

- `dbSortArabic` 使用阿拉伯文排序次序。

- `dbSortCyrillic` 使用俄文排序次序。

- `dbSortCzech` 使用捷克文排序次序。

- `dbSortDutch` 使用荷蘭文排序次序。

- `dbSortGreek` 使用希臘文排序次序。

- `dbSortHebrew` 使用希伯來文排序次序。

- `dbSortHungarian` 使用匈牙利文排序次序。

- `dbSortIcelandic` 使用冰島排序次序。

- `dbSortNorwdan` 使用挪威文或丹麥文排序次序。

- `dbSortPDXIntl` 使用 Paradox 國際排序次序。

- `dbSortPDXNor` 使用 Paradox 挪威或丹麥文排序次序。

- `dbSortPDXSwe` 使用 Paradox 瑞典文或芬蘭文排序次序。

- `dbSortPolish` 使用波蘭文排序次序。

- `dbSortSpanish` 使用西班牙文排序次序。

- `dbSortSwedFin` 使用瑞典文或芬蘭文排序次序。

- `dbSortTurkish` 使用土耳其文排序次序。

- `dbSortUndefined` 排序次序未定義或不明。

如需詳細資訊，請參閱 DAO 說明中的「自訂資料存取的 Windows 登錄設定」主題。

*m_nQueryTimeout*<br/>
在 ODBC 資料庫上執行查詢時，Microsoft Jet 資料庫引擎在逾時錯誤發生前等待的秒數。 預設的超時值為60秒。 當 QueryTimeout 設定為0時，不會發生任何超時;這可能會導致程式停止回應。 若要直接取得這個屬性的值，請呼叫資料庫物件的[GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout)成員函式。 如需詳細資訊，請參閱 DAO 說明中的「QueryTimeout 屬性」主題。

*m_strConnect*<br/>
提供開啟資料庫之來源的相關資訊。 如需連接字串的詳細資訊，以及如需直接抓取此屬性值的相關資訊，請參閱[CDaoDatabase：： GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect)成員函式。 如需詳細資訊，請參閱 DAO 說明中的「連接屬性」主題。

## <a name="remarks"></a>備註

資料庫是一個 DAO 物件，其基礎為[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)類別的 MFC 物件。 主要、次要和以上的參考會指出[CDaoWorkspace：： oomads.getdatabaseinfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo)成員函式傳回信息的方式。

[CDaoWorkspace：： oomads.getdatabaseinfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo)成員函式所取出的資訊會儲存在 `CDaoDatabaseInfo` 結構中。 針對在其資料庫集合中儲存資料庫物件的 `CDaoWorkspace` 物件呼叫 `GetDatabaseInfo`。 `CDaoDatabaseInfo` 也會在 debug build 中定義 `Dump` 成員函式。 您可以使用 `Dump` 來傾印 `CDaoDatabaseInfo` 物件的內容。

## <a name="requirements"></a>需求

**標頭：** afxdao。h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace 類別](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)
