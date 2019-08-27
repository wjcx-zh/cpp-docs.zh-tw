---
title: COM+ 1.0, ATL COM+ 1.0 元件精靈
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.mts.options
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
ms.openlocfilehash: 83b7beafe537f6b271b254d16505b515a41acf27
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496697"
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0, ATL COM+ 1.0 元件精靈

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供此精靈。

::: moniker-end

::: moniker range="<=vs-2017"

使用「ATL COM+ 1.0 元件精靈」的這個頁面來指定介面類型，以及要支援的額外介面。

如需有關 ATL 專案和 ATL COM 類別的詳細資訊，請參閱 [ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)。

- **Interface**

   指出物件所支援的介面類型。 物件預設會支援雙重介面。

   |選項|描述|
   |------------|-----------------|
   |**雙重**|指定物件支援雙重介面 (其 vtable 具有自訂介面函式和晚期繫結 `IDispatch` 方法)。 同時允許 COM 用戶端和自動化控制器存取物件。|
   |**自訂**|指定物件支援自訂介面 (其 vtable 具有自訂介面函式)。 自訂介面執行速度比雙重介面快，特別是跨處理序界限時。<br /><br /> - **自動化相容** 為自訂介面新增自動化支援。 針對屬性專案，會在 coclass 中設定 **oleautomation** 屬性。|

- **可排入佇列**

   指出用戶端可以使用訊息佇列，以非同步方式呼叫此元件。 將元件屬性化巨集 custom(TLBATTR_QUEUEABLE, 0) 新增至 .h 檔案 (屬性化專案) 或 .idl 檔案 (非屬性化專案)。

- **支援**

   指出有適用於錯誤處理和物件控制的額外支援。

   |選項|描述|
   |------------|-----------------|
   |**ISupportErrorInfo**|建立適用於 [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) 介面的支援，以便讓物件將錯誤資訊傳回給用戶端。|
   |**IObjectControl**|將您的物件類別提供給三個 [IObjectControl](/windows/win32/api/comsvcs/nn-comsvcs-iobjectcontrol) 方法：[Activate](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-activate)、[CanBePooled](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-canbepooled) 及 [Deactivate](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-deactivate)。|
   |**IObjectConstruct**|建立適用於 [IObjectConstruct](/windows/win32/api/comsvcs/nn-comsvcs-iobjectconstruct) 介面的支援，以管理從其他方法或物件傳入參數。|

- **異動**

   指出物件支援交易。 在 .idl 檔案 (非屬性化專案) 中包含 mtxattr.h 檔案。

   |選項|描述|
   |------------|-----------------|
   |**支援**|藉由將元件屬性巨集 custom(TLBATTR_TRANS_SUPPORTED,0) 新增至 .h 檔案 (屬性化專案) 或 .idl 檔案 (非屬性化專案)，指定物件一律不是交易資料流的根。|
   |**必要**|藉由將元件屬性巨集 custom(TLBATTR_TRANS_REQUIRED,0) 新增至 .h 檔案 (屬性化專案) 或 .idl 檔案 (非屬性化專案)，指定物件可以是或不可以是交易資料流的根。|
   |**不支援**|指定物件排除交易。 將元件屬性巨集 custom(TLBATTR_TRANS_NOTSUPP,0) 新增至 .h 檔案 (屬性化專案) 或 .idl 檔案 (非屬性化專案)。|
   |**需要新增**|藉由將元件屬性巨集 custom(TLBATTR_TRANS_REQNEW,0) 新增至 .h 檔案 (屬性化專案) 或 .idl 檔案 (非屬性化專案)，指定物件一律是交易資料流的根。|

::: moniker-end

## <a name="see-also"></a>另請參閱

[ATL COM+ 1.0 元件精靈](../../atl/reference/atl-com-plus-1-0-component-wizard.md)<br/>
[ATL COM+ 1.0 元件](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
