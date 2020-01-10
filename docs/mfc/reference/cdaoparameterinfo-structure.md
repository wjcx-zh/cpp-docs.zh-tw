---
title: CDaoParameterInfo 結構
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 9f96cba8ea43db7e24e834b1de4ffb593b2c6e0d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303491"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo 結構

`CDaoParameterInfo` 結構包含針對資料存取物件（DAO）定義之參數物件的相關資訊。 DAO 3.6 是最後的版本，被視為已淘汰。

## <a name="syntax"></a>語法

```
struct CDaoParameterInfo
{
    CString m_strName;       // Primary
    short m_nType;           // Primary
    ColeVariant m_varValue;  // Secondary
};
```

#### <a name="parameters"></a>參數

*m_strName*<br/>
唯一具名引數物件。 如需詳細資訊，請參閱 DAO 說明中的「名稱屬性」主題。

*m_nType*<br/>
值，指出參數物件的資料類型。 如需可能值的清單，請參閱[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構的*m_nType*成員。 如需詳細資訊，請參閱 DAO 說明中的「類型屬性」主題。

*m_varValue*<br/>
參數的值，儲存在[COleVariant](../../mfc/reference/colevariant-class.md)物件中。

## <a name="remarks"></a>備註

上述主要和次要的參考會指出[GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)成員函式在類別 `CDaoQueryDef`中傳回信息的方式。

MFC 不會在類別中封裝 DAO 參數物件。 基本 MFC `CDaoQueryDef` 物件的 DAO querydef 物件會在其參數集合中儲存參數。 若要存取[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)物件中的參數物件，請呼叫 querydef 物件的 `GetParameterInfo` 成員函式，以取得特定參數名稱或索引至參數集合。 您可以使用[CDaoQueryDef：： GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount)成員函式搭配 `GetParameterInfo`，以在參數集合中執行迴圈。

[CDaoQueryDef：： GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)成員函式所取出的資訊會儲存在 `CDaoParameterInfo` 結構中。 呼叫中的 querydef 物件 `GetParameterInfo`，其參數集合中會儲存參數物件。

> [!NOTE]
>  如果您只想要取得或設定參數的值，請使用 `CDaoRecordset`類別的[GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue)和[SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue)成員函式。

`CDaoParameterInfo` 也會在 debug build 中定義 `Dump` 成員函式。 您可以使用 `Dump` 來傾印 `CDaoParameterInfo` 物件的內容。

## <a name="requirements"></a>需求

**標頭：** afxdao。h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)
