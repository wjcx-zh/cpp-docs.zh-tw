---
title: CDaoErrorInfo 結構
ms.date: 09/17/2019
f1_keywords:
- CDaoErrorInfo
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
ms.openlocfilehash: 8d731c8e8bea1adc850ab3c00c7688b9f8c9b819
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304228"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo 結構

`CDaoErrorInfo` 結構包含針對資料存取物件（DAO）定義之錯誤物件的相關資訊。 DAO 3.6 是最後的版本，被視為已淘汰。

## <a name="syntax"></a>語法

```
struct CDaoErrorInfo
{
    long m_lErrorCode;
    CString m_strSource;
    CString m_strDescription;
    CString m_strHelpFile;
    long m_lHelpContext;
};
```

#### <a name="parameters"></a>參數

*m_lErrorCode*<br/>
數值 DAO 錯誤碼。 請參閱 DAO 說明中的「可捕獲的資料存取錯誤」主題。

*m_strSource*<br/>
原先產生錯誤之物件或應用程式的名稱。 Source 屬性會指定字串運算式，代表原本產生錯誤的物件。運算式通常是物件的類別名稱。 如需詳細資訊，請參閱 DAO 說明中的「來源屬性」主題。

*m_strDescription*<br/>
與錯誤相關聯的描述性字串。 如需詳細資訊，請參閱 DAO 說明中的「描述屬性」主題。

*m_strHelpFile*<br/>
Microsoft Windows 說明檔的完整路徑。 如需詳細資訊，請參閱 DAO 說明中的「HelpCoNtext，協助程式屬性」主題。

*m_lHelpCoNtext*<br/>
Microsoft Windows 說明檔中主題的內容識別碼。 如需詳細資訊，請參閱 DAO 說明中的「HelpCoNtext，協助程式屬性」主題。

## <a name="remarks"></a>備註

MFC 不會將 DAO 錯誤物件封裝在類別中。 相反地， [CDaoException](../../mfc/reference/cdaoexception-class.md)類別會提供介面來存取 DAO `DBEngine` 物件中包含的錯誤集合，也就是包含所有工作區的物件。 當 MFC DAO 作業擲回您捕捉的 `CDaoException` 物件時，MFC 會填入 `CDaoErrorInfo` 結構，並將它儲存在例外狀況物件的[m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo)成員中。 （如果您選擇直接呼叫 DAO，您必須自行呼叫例外狀況物件的[GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo)成員函式，以填滿 `m_pErrorInfo`）。

如需處理 DAO 錯誤的詳細資訊，請參閱[例外狀況：資料庫例外](../../mfc/exceptions-database-exceptions.md)狀況。 如需相關資訊，請參閱 DAO 說明中的「錯誤物件」主題。

[CDaoException：： GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo)成員函式所取出的資訊會儲存在 `CDaoErrorInfo` 結構中。 從您在例外狀況處理常式中攔截的 `CDaoException` 物件，檢查[m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo)的資料成員，或從您明確建立的 `CDaoException` 物件呼叫 `GetErrorInfo`，以便檢查 DAO 介面的直接呼叫期間可能發生的錯誤。 `CDaoErrorInfo` 也會在 debug build 中定義 `Dump` 成員函式。 您可以使用 `Dump` 來傾印 `CDaoErrorInfo` 物件的內容。

## <a name="requirements"></a>需求

**標頭：** afxdao。h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoException 類別](../../mfc/reference/cdaoexception-class.md)
