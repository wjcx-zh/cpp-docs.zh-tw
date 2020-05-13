---
title: CFileTimeSpan 類別
description: 活動範本庫 (ATL) 和 Microsoft 基礎類 (MFC) CFileTimeSpan 類以 FILETIME 單位為單位管理時間間隔。
ms.date: 01/10/2020
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
ms.openlocfilehash: 87737ea1c778660a68510b484bcdfa3a4670e8ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317859"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan 類別

此類提供用於管理與檔關聯的相對日期和時間值的方法。

## <a name="syntax"></a>語法

```cpp
class CFileTimeSpan
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[檔案時間跨度::檔案時間跨度](#cfiletimespan)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[檔案時間跨度:取得時間跨度](#gettimespan)|調用此方法以從`CFileTimeSpan`物件檢索時間跨度。|
|[檔案時間跨度::設定時間跨度](#settimespan)|調用此方法以設置`CFileTimeSpan`物件的時間跨度。|

### <a name="public-operators"></a>公共運營商

|名稱|描述|
|----------|-----------------|
|[檔案時間跨度::運算子 -](#operator_-)|對`CFileTimeSpan`物件執行減法。|
|[時間跨度::操作員!*](#operator_neq)|比較兩個 `CFileTimeSpan` 物件是否不相等。|
|[時間跨度::操作員 |](#operator_add)|對`CFileTimeSpan`物件執行添加。|
|[時間跨度::操作員 |](#operator_add_eq)|對`CFileTimeSpan`物件執行添加,並將結果分配給當前物件。|
|[檔案時間跨度::運算子&lt;](#operator_lt)|比較兩`CFileTimeSpan`個物件以確定較小的物件。|
|[檔案時間跨度::運算子&lt;=](#operator_lt_eq)|比較兩`CFileTimeSpan`個物件以確定相等性或較小的物件。|
|[時間跨度::運算符 |](#operator_eq)|分配運算符。|
|[檔案時間跨度::運算符 -*](#operator_-_eq)|對`CFileTimeSpan`物件執行減法,並將結果分配給當前物件。|
|[時間跨度::運算符 |](#operator_eq_eq)|比較兩個 `CFileTimeSpan` 物件是否相等。|
|[檔案時間跨度::運算子&gt;](#operator_gt)|比較兩`CFileTimeSpan`個物件以確定較大的物件。|
|[檔案時間跨度::運算子&gt;=](#operator_gt_eq)|比較兩`CFileTimeSpan`個物件以確定相等性或較大。|

## <a name="remarks"></a>備註

該`CFileTimeSpan`類提供了處理檔系統使用單位中相對時間段的方法。 這些單元通常用於檔操作,例如創建檔、上次訪問或上次修改文件的時間。 此類的方法經常與[CFileTime 類](../../atl-mfc-shared/reference/cfiletime-class.md)物件結合使用。

## <a name="example"></a>範例

請參考[CFileTime::毫秒的範例](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond)。

## <a name="requirements"></a>需求

**標題:** atltime.h

## <a name="cfiletimespancfiletimespan"></a><a name="cfiletimespan"></a>檔案時間跨度::檔案時間跨度

建構函式。

```cpp
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>參數

*跨度*\
現有的 `CFileTimeSpan` 物件。

*恩斯潘*\
以 FILETIME 單位為單位的時間段。

### <a name="remarks"></a>備註

可以使用`CFileTimeSpan`現有`CFileTimeSpan`物件創建物件,或以 100 納秒的 FILETIME 單位表示為 64 位元值。 有關詳細資訊,請參閱[CFileTime](cfiletime-class.md)。 默認構造函數將時間跨度設置為 0。

## <a name="cfiletimespangettimespan"></a><a name="gettimespan"></a>檔案時間跨度:取得時間跨度

調用此方法以從`CFileTimeSpan`物件檢索時間跨度。

```cpp
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>傳回值

返回以 100 納秒 FILETIME 單位為單位的時間跨度。 有關詳細資訊,請參閱[CFileTime](cfiletime-class.md)。

## <a name="cfiletimespanoperator--"></a><a name="operator_-"></a>檔案時間跨度::運算子 -

對`CFileTimeSpan`物件執行減法。

```cpp
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*跨度*\
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

返回表示`CFileTimeSpan`兩個時間跨度之間差值結果的物件。

## <a name="cfiletimespanoperator-"></a><a name="operator_neq"></a>時間跨度::操作員!*

比較兩個 `CFileTimeSpan` 物件是否不相等。

```cpp
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*跨度*\
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果要比較的項不等於物件,`CFileTimeSpan`則返回 TRUE;否則 FALSE。

## <a name="cfiletimespanoperator-"></a><a name="operator_add"></a>時間跨度::操作員 |

對`CFileTimeSpan`物件執行添加。

```cpp
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*跨度*\
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

返回包含`CFileTimeSpan`兩個時間跨度總和的物件。

## <a name="cfiletimespanoperator-"></a><a name="operator_add_eq"></a>時間跨度::操作員 |

對`CFileTimeSpan`物件執行添加,並將結果分配給當前物件。

```cpp
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*跨度*\
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

返回包含兩`CFileTimeSpan`個時間跨度總和的更新物件。

## <a name="cfiletimespanoperator-lt"></a><a name="operator_lt"></a>檔案時間跨度::運算子&lt;

比較兩`CFileTimeSpan`個物件以確定較小的物件。

```cpp
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*跨度*\
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件小於第二個物件(即表示較短的時間段),則返回 TRUE,否則為 FALSE。

## <a name="cfiletimespanoperator-lt"></a><a name="operator_lt_eq"></a>檔案時間跨度::運算子&lt;=

比較兩`CFileTimeSpan`個物件以確定相等性或較小的物件。

```cpp
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*跨度*\
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件小於(即表示較短的時間段)或等於第二個物件,否則為 FALSE,則返回 TRUE。

## <a name="cfiletimespanoperator-"></a><a name="operator_eq"></a>時間跨度::運算符 |

分配運算符。

```cpp
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>參數

*跨度*\
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

返回更新`CFileTimeSpan`的物件。

## <a name="cfiletimespanoperator--"></a><a name="operator_-_eq"></a>檔案時間跨度::運算符 -*

對`CFileTimeSpan`物件執行減法,並將結果分配給當前物件。

```cpp
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*跨度*\
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

返回更新`CFileTimeSpan`的物件。

## <a name="cfiletimespanoperator-"></a><a name="operator_eq_eq"></a>時間跨度::運算符 |

比較兩個 `CFileTimeSpan` 物件是否相等。

```cpp
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*跨度*\
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果物件相等,則返回 TRUE,否則為 FALSE。

## <a name="cfiletimespanoperator-gt"></a><a name="operator_gt"></a>檔案時間跨度::運算子&gt;

比較兩`CFileTimeSpan`個物件以確定較大的物件。

```cpp
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*跨度*\
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件大於(即表示較長的時間段)大於第二個對象(否則 FALSE),則返回 TRUE。

## <a name="cfiletimespanoperator-gt"></a><a name="operator_gt_eq"></a>檔案時間跨度::運算子&gt;=

比較兩`CFileTimeSpan`個物件以確定相等性或較大。

```cpp
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*跨度*\
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件大於(即表示較長的時間段)或等於第二個物件,否則為 FALSE,則返回 TRUE。

## <a name="cfiletimespansettimespan"></a><a name="settimespan"></a>檔案時間跨度::設定時間跨度

調用此方法以設置`CFileTimeSpan`物件的時間跨度。

```cpp
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>參數

*恩斯潘*\
時間跨度的新值(以100納秒的FILETIME單位為單位)。 有關詳細資訊,請參閱[CFileTime](cfiletime-class.md)。

## <a name="see-also"></a>另請參閱

[檔案時間](/windows/win32/api/minwinbase/ns-minwinbase-filetime)\
[檔案時間類別](cfiletime-class.md)\
[層次結構圖表](../../mfc/hierarchy-chart.md)\
[ATL/MFC 共用類](../../atl-mfc-shared/atl-mfc-shared-classes.md)
