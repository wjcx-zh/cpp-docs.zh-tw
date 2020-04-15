---
title: CComAuto關鍵科類別
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 8cbf08082fd24ef2cf0e8794e2944a799baec084
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321096"
---
# <a name="ccomautocriticalsection-class"></a>CComAuto關鍵科類別

`CComAutoCriticalSection`提供了獲取和釋放關鍵部分物件擁有權的方法。

## <a name="syntax"></a>語法

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCom自動臨界部分:cCom自動臨界部分](#ccomautocriticalsection)|建構函式。|
|[CCom自動臨界部分::_CCom自動臨界部分](#dtor)|解構函式。|

## <a name="remarks"></a>備註

`CComAutoCriticalSection`與類[CCom臨界節](../../atl/reference/ccomcriticalsection-class.md)類似`CComAutoCriticalSection`,除了在構造函數中自動初始化關鍵截面物件。

通常,您可以`typedef`通過`CComAutoCriticalSection`名稱[「自動關鍵節](ccommultithreadmodel-class.md#autocriticalsection)」 來使用 。 此名稱引用`CComAutoCriticalSection`時,使用[CComMultiThreadModel。](../../atl/reference/ccommultithreadmodel-class.md)

使用`Init`此類`Term`時[,CCom臨界節](../../atl/reference/ccomcriticalsection-class.md)中的和 方法不可用。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CCom 臨界部分](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>需求

**標題:** atlcore.h

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="ccomautocriticalsection"></a>CCom自動臨界部分:cCom自動臨界部分

建構函式。

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>備註

調用 Win32 函數[初始化關鍵節](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection),它初始化關鍵節物件。

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="dtor"></a>CCom自動臨界部分::_CCom自動臨界部分

解構函式。

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>備註

析構函數調用[Delete關鍵節](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection),它釋放關鍵節物件使用的所有系統資源。

## <a name="see-also"></a>另請參閱

[CComFake臨界科類](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[CCom臨界節類](../../atl/reference/ccomcriticalsection-class.md)
