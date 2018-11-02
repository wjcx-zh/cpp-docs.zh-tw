---
title: CDaoParameterInfo 結構
ms.date: 11/04/2016
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 29248f04833662750d99b112fe2386c6ff4d97fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545908"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo 結構

`CDaoParameterInfo`結構包含的資料存取物件 (DAO) 定義的參數物件的相關資訊。

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
唯一名稱的參數物件。 如需詳細資訊，請參閱主題 DAO [說明] 中的 「 名稱屬性 」。

*m_nType*<br/>
值，指出參數物件的資料類型。 如需可能的值，請參閱*m_nType*隸屬[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。 如需詳細資訊，請參閱主題 DAO [說明] 中的 「 型別屬性 」。

*m_varValue*<br/>
參數的值，儲存在[COleVariant](../../mfc/reference/colevariant-class.md)物件。

## <a name="remarks"></a>備註

主要和次要上述的參考會指出所傳回的資訊是如何[GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)類別中的成員函式`CDaoQueryDef`。

MFC 不會封裝 DAO 類別中的參數物件。 DAO recordset 物件基礎的 MFC`CDaoQueryDef`物件會將參數儲存在其參數的集合。 若要存取中的參數物件[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)物件，請呼叫 recordset 物件的`GetParameterInfo`特定的參數名稱或索引的參數集合的成員函式。 您可以使用[CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount)成員函式中搭配`GetParameterInfo`Parameters 集合執行迴圈。

所擷取的資訊[CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)成員函式會儲存在`CDaoParameterInfo`結構。 呼叫`GetParameterInfo`recordset 物件，其參數集合中儲存的參數物件。

> [!NOTE]
>  如果您想要取得或設定參數的值，請使用[GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue)並[SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue)類別成員函式`CDaoRecordset`。

`CDaoParameterInfo` 也會定義`Dump`成員函式，在偵錯組建。 您可以使用`Dump`傾印的內容`CDaoParameterInfo`物件。

## <a name="requirements"></a>需求

**標頭：** afxdao.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)
