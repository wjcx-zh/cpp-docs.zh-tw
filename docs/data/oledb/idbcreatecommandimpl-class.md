---
title: IDBCreateCommandImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- IDBCreateCommandImpl::CreateCommand
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
ms.openlocfilehash: b7b658b2b365eb84a39ae94cef7c77e18d7bd4a0
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845545"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl 類別

提供 [IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85)) 介面的實作為。

## <a name="syntax"></a>語法

```cpp
template <class T, class CommandClass >
class ATL_NO_VTABLE IDBCreateCommandImpl
   : public IDBCreateCommand
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自的會話物件 `IDBCreateCommandImpl` 。

*CommandClass*<br/>
命令類別。

## <a name="requirements"></a>規格需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

| 名稱 | 描述 |
|-|-|
|[CreateCommand](#createcommand)|建立新的命令。|

## <a name="remarks"></a>備註

會話物件上的選擇性介面，用來取得新的命令。

## <a name="idbcreatecommandimplcreatecommand"></a><a name="createcommand"></a> IDBCreateCommandImpl：： CreateCommand

建立新的命令，並傳回所要求的介面。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppvCommand);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IDBCreateCommand：： CreateCommand](/previous-versions/windows/desktop/ms709772(v=vs.85)) 。

某些參數會對應至不同名稱 OLE DB 程式設計 *人員參考* 參數，如中所述 `IDBCreateCommand::CreateCommand` ：

|OLE DB 範本參數|*OLE DB 程式設計人員的參考* 參數|
|--------------------------------|------------------------------------------------|
|*ppvCommand*|*ppCommand*|

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
