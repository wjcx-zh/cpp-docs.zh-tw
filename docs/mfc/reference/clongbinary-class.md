---
title: CLongBinary 類別
ms.date: 11/04/2016
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
ms.openlocfilehash: 94666c0d15898e05ae78663a15d86b7d00d5c9c6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505678"
---
# <a name="clongbinary-class"></a>CLongBinary 類別

簡化在資料庫中對極大型二進位資料物件 (通常稱為 BLOB 或「二進位大型物件」) 的處理。

## <a name="syntax"></a>語法

```
class CLongBinary : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CLongBinary::CLongBinary](#clongbinary)|建構 `CLongBinary` 物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|包含其控制碼儲存所在`m_hData`之資料物件的實際大小 (以位元組為單位)。|
|[CLongBinary::m_hData](#m_hdata)|包含實際影像物件的 Windows HGLOBAL 控制碼。|

## <a name="remarks"></a>備註

例如, SQL 資料表中的記錄欄位可能包含代表圖片的點陣圖。 `CLongBinary`物件會儲存這類物件, 並持續追蹤其大小。

> [!NOTE]
>  一般來說, 最好的做法是將[CByteArray](../../mfc/reference/cbytearray-class.md)與[DFX_Binary](record-field-exchange-functions.md#dfx_binary)函數搭配使用。 您仍然可以使用`CLongBinary`, 但在 Win32 `CByteArray`中, 一般會提供更多功能, 因為已不再有16位`CByteArray`所遇到的大小限制。 這套建議適用于使用資料存取物件 (DAO) 以及開放式資料庫連接 (ODBC) 進行程式設計。

若要使用`CLongBinary`物件, 請在您的記錄集類別`CLongBinary`中宣告類型的欄位資料成員。 這個成員將是記錄集類別的內嵌成員, 並且會在結構化記錄集時進行結構化。 在`CLongBinary`建立物件之後, 記錄欄位交換 (RFX) 機制會從資料來源上目前記錄中的欄位載入資料物件, 並在記錄更新時將其儲存回記錄。 RFX 會查詢二進位大型物件大小的資料來源、為其`CLongBinary`配置儲存區 (透過物件的`m_hData`資料成員`HGLOBAL` ), 並將控制碼儲存至中`m_hData`的資料。 RFX 也會將資料物件的實際大小儲存在`m_dwDataLength`資料成員中。 使用您通常用來操作儲存在`m_hData`Windows `HGLOBAL`控制碼中之資料的相同技術, 透過來處理物件中的資料。

當您終結記錄集時, 內嵌`CLongBinary`物件也會終結, 而且其析構函`HGLOBAL`式會解除配置資料控制碼。

如需大型物件和使用的`CLongBinary`詳細資訊, 請參閱文章[記錄集 (ODBC)](../../data/odbc/recordset-odbc.md)和[記錄集:使用大型資料項目 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>需求

**標頭:** afxdb_。h

##  <a name="clongbinary"></a>CLongBinary:: CLongBinary

建構 `CLongBinary` 物件。

```
CLongBinary();
```

##  <a name="m_dwdatalength"></a>CLongBinary:: m_dwDataLength

將儲存在 HGLOBAL 控制碼中的資料實際大小 (以位元組為`m_hData`單位) 儲存在中。

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>備註

這個大小可能小於配置給資料的記憶體區塊大小。 呼叫 Win32 [GLobalSize](/windows/win32/api/winbase/nf-winbase-globalsize)函式以取得配置的大小。

##  <a name="m_hdata"></a>CLongBinary:: m_hData

將 Windows HGLOBAL 控制碼儲存至實際的二進位大型物件資料。

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
