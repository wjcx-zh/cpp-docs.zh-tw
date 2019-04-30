---
title: CDaoDatabaseInfo 結構
ms.date: 11/04/2016
f1_keywords:
- CDaoDatabaseInfo
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
ms.openlocfilehash: 920301af6f660aeac010ecbf844b80ea628bbfd7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405764"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo 結構

`CDaoDatabaseInfo`結構包含的資料存取物件 (DAO) 定義的資料庫物件的相關資訊。

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
唯一名稱的資料庫物件。 若要直接擷取此屬性，請呼叫[CDaoDatabase::GetName](../../mfc/reference/cdaodatabase-class.md#getname)。 如需詳細資訊，請參閱 DAO [說明] 中的 「 名稱屬性 」。

*m_bUpdatable*<br/>
指出是否可以對資料庫進行變更。 若要直接擷取此屬性，請呼叫[CDaoDatabase::CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate)。 如需詳細資訊，請參閱 DAO [說明] 中的 「 可更新屬性 」。

*m_bTransactions*<br/>
指出資料來源是否支援交易，錄製一系列的稍後復原回來的變更 （取消） 或認可 （儲存）。 如果資料庫以 Microsoft Jet 資料庫引擎為基礎，交易屬性為非零值，而且您可以使用交易。 其他資料庫引擎可能不支援交易。 若要直接擷取此屬性，請呼叫[CDaoDatabase::CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact)。 如需詳細資訊，請參閱 DAO [說明] 中的 「 交易屬性 」。

*m_strVersion*<br/>
表示 Microsoft Jet 資料庫引擎的版本。 若要直接擷取這個屬性的值，呼叫資料庫物件的[GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion)成員函式。 如需詳細資訊，請參閱 DAO [說明] 中的 「 版本屬性 」。

*m_lCollatingOrder*<br/>
指定文字字串比較或排序的排序次序的順序。 可能的值包括：

- `dbSortGeneral` 使用一般 （英文、 法文、 德文、 葡萄牙文、 義大利文、 和現代的西班牙文） 的排序順序。

- `dbSortArabic` 使用阿拉伯文排序次序。

- `dbSortCyrillic` 使用俄文的排序次序。

- `dbSortCzech` 使用捷克文的排序次序。

- `dbSortDutch` 使用荷蘭的排序次序。

- `dbSortGreek` 使用希臘文的排序次序。

- `dbSortHebrew` 使用希伯來文排序次序。

- `dbSortHungarian` 使用匈牙利的排序次序。

- `dbSortIcelandic` 使用 Icelandic 的排序次序。

- `dbSortNorwdan` 使用挪威或丹麥的排序次序。

- `dbSortPDXIntl` 使用 Paradox 國際排序順序。

- `dbSortPDXNor` 使用 Paradox 挪威或丹麥的排序次序。

- `dbSortPDXSwe` 使用 Paradox 瑞典文或芬蘭文的排序次序。

- `dbSortPolish` 使用波蘭文的排序次序。

- `dbSortSpanish` 使用西班牙文的排序次序。

- `dbSortSwedFin` 使用瑞典文或芬蘭文的排序次序。

- `dbSortTurkish` 使用土耳其文的排序次序。

- `dbSortUndefined` 未定義或未知的排序次序。

如需詳細資訊，請參閱本主題中的 < 自訂 Windows 登錄設定的資料存取 」 DAO 幫助。

*m_nQueryTimeout*<br/>
ODBC 資料庫上執行查詢時，就會發生 Microsoft Jet 資料庫引擎在逾時錯誤之前等候的秒數。 預設逾時值為 60 秒。 當 QueryTimeout 設定為 0 時，不會逾時，就會發生;這會造成程式停止回應。 若要直接擷取這個屬性的值，呼叫資料庫物件的[GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout)成員函式。 如需詳細資訊，請參閱 DAO [說明] 中的 < QueryTimeout 屬性 >。

*m_strConnect*<br/>
提供的已開啟的資料庫來源的相關資訊。 如需資訊即將連接字串，和直接擷取值，這個屬性的相關資訊，請參閱[CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect)成員函式。 如需詳細資訊，請參閱主題 DAO [說明] 中的 [連接屬性]。

## <a name="remarks"></a>備註

資料庫是基礎類別的 MFC 物件的 DAO 物件[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)。 主要、 次要資料庫，且上述所有的參考會指出所傳回的資訊是如何[CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo)成員函式。

所擷取的資訊[CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo)成員函式會儲存在`CDaoDatabaseInfo`結構。 呼叫`GetDatabaseInfo`針對`CDaoWorkspace`資料庫物件會儲存其資料庫集合中的物件。 `CDaoDatabaseInfo` 也會定義`Dump`成員函式，在偵錯組建。 您可以使用`Dump`傾印的內容`CDaoDatabaseInfo`物件。

## <a name="requirements"></a>需求

**標頭：** afxdao.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace 類別](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)
