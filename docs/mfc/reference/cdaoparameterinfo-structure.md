---
title: CDaoParameterInfo 結構
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 6d594bbeec34e400eb074c136e3467e78b35c4ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368973"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo 結構

該`CDaoParameterInfo`結構包含有關為數據存取物件 (DAO) 定義的參數物件的資訊。 DAO 3.6 是最終版本,它被視為過時版本。

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
唯一地命名參數物件。 有關詳細資訊,請參閱 DAO 説明中的主題"名稱屬性"。

*m_nType*<br/>
指示參數物件的數據類型的值。 有關可能值的清單,請參閱[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構*的m_nType*成員。 有關詳細資訊,請參閱 DAO 説明中的主題"類型屬性"。

*m_varValue*<br/>
存儲在[COleVariant](../../mfc/reference/colevariant-class.md)物件中的參數的值。

## <a name="remarks"></a>備註

對上述主要和次要的引用指示類`CDaoQueryDef`中的[GetparameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)成員函數如何返回資訊。

MFC 不封裝類中的 DAO 參數物件。 DAO 查詢def 物件`CDaoQueryDef`的基礎 MFC 物件在其參數集合中存儲參數。 要造[訪 CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)物件中的參數物件,請將特定`GetParameterInfo`參數名稱的 querydef 物件的成員函數或索引呼叫到參數集合中。 您可以使用[CDaoQueryDef::獲取參數計數](../../mfc/reference/cdaoquerydef-class.md#getparametercount)成員函數`GetParameterInfo`,並結合迴圈通過參數集合。

[CDaoQueryDef檢索的資訊:獲取參數資訊](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)成員函數存儲`CDaoParameterInfo`在結構 中。 調用`GetParameterInfo`儲存參數物件的查詢def物件。

> [!NOTE]
> 如果只想獲取或設置參數的值,請使用類`CDaoRecordset`的[GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue)和[SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue)成員函數。

`CDaoParameterInfo`還在調試生成中`Dump`定義成員函數。 可以使用`Dump`轉`CDaoParameterInfo`儲 對象的內容。

## <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)
