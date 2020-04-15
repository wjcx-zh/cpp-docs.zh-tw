---
title: IAxwin 環境排程Ex 介面
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: f4816846801e388619db62998ec979a1100916ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329985"
---
# <a name="iaxwinambientdispatchex-interface"></a>IAxwin 環境排程Ex 介面

此介面為托管控件實現補充環境屬性。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[設定環境排程](#setambientdispatch)|呼叫此方法是為了使用使用者定義的介面補充預設環境屬性介面。|

## <a name="remarks"></a>備註

此介面包含在以靜態連結到 ATL 和主機 ActiveX 控件的 ATL 應用程式中,尤其是具有環境屬性的 ActiveX 控制件。 不包括此介面將生成此斷言:"您是否忘記將 LIBID 傳遞給 CComModule::Init"

此介面由 ATL 的 ActiveX 控制項託管物件公開。 派生自[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md),`IAxWinAmbientDispatchEx`添加了一種方法,允許您用您自己的一種來補充 ATL 提供的環境屬性介面。

<xref:System.Windows.Forms.AxHost>將嘗試載入有關`IAxWinAmbientDispatch`和`IAxWinAmbientDispatchEx`從包含代碼的類型庫的類型資訊。

如果要連結到 ATL90.dll,AXHost 將從 DLL 中的類型庫中載**AXHost**入類型資訊。

有關詳細資訊[,請參閱使用 ATL AXHost 託管 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md)。

## <a name="requirements"></a>需求

此介面的定義有多種形式可用,如下表所示。

|定義類型|檔案|
|---------------------|----------|
|Idl|atliface.idl|
|類型庫|ATL.dll|
|C++|atliface.h (也包含在 ATLBase.h 中)|

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a>IAxwin 環境排程Ex::設定環境排程

呼叫此方法是為了使用使用者定義的介面補充預設環境屬性介面。

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>參數

*pDispatch*<br/>
指向新介面的指標。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

當`SetAmbientDispatch`使用指向新介面的指標調用時,如果[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)尚未提供這些屬性,則此新介面將用於調用托管控件要求的任何屬性或方法。

## <a name="see-also"></a>另請參閱

[IAxWin 環境排程介面](../../atl/reference/iaxwinambientdispatch-interface.md)
