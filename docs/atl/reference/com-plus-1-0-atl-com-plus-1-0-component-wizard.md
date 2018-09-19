---
title: COM + 1.0，ATL COM + 1.0 元件精靈 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.options
dev_langs:
- C++
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 471d6a273bfb4a446dbf5aba1c3b1bb31d988b24
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116096"
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0, ATL COM+ 1.0 元件精靈

使用 ATL COM + 1.0 元件精靈的這個頁面來指定支援的介面型別和其他介面。

如需有關 ATL 專案和 ATL COM 類別的詳細資訊，請參閱[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)。

- **Interface**

   表示物件支援的介面的型別。 根據預設，物件會支援雙重介面。

   |選項|描述|
   |------------|-----------------|
   |**雙重**|指定物件是否支援雙重介面 (其 vtable 具有自訂介面函式和晚期繫結`IDispatch`方法)。 可讓 COM 用戶端和 Automation 控制器存取的物件。|
   |**自訂**|指定物件支援自訂介面 （其 vtable 有自訂介面函式）。 自訂介面可以是較快，雙重介面，尤其是跨處理序界限。<br /><br /> -   **Automation 相容**自動化支援加入自訂的介面。 針對屬性化專案，設定**oleautomation**中 coclass 的屬性。|

- **Queueable**

   表示用戶端可以呼叫此元件以非同步方式使用訊息佇列。 .H 檔 （屬性化專案） 或.idl 檔案 （非屬性化專案），請加入元件屬性巨集自訂 (TLBATTR_QUEUEABLE，0)。

- **支援**

   表示錯誤處理和物件控制的其他支援。

   |選項|描述|
   |------------|-----------------|
   |**ISupportErrorInfo**|建立支援[ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md)介面讓物件可以將錯誤資訊傳回給用戶端。|
   |**IObjectControl**|提供三個您物件的存取[IObjectControl](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectcontrol)方法： [Activate](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-activate)， [CanBePooled](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-canbepooled)，以及[停用](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-deactivate)。|
   |**IObjectConstruct**|建立支援[IObjectConstruct](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectconstruct)介面，以管理傳遞中的其他方法或物件中的參數。|

- **異動**

   指出物件支援交易。 包含檔案 mtxattr.h.idl 檔案 （非屬性化專案） 中。

   |選項|描述|
   |------------|-----------------|
   |**支援**|指定物件永遠不會交易資料流的根目錄加入元件的屬性巨集 custom(TLBATTR_TRANS_SUPPORTED,0).h 檔 （屬性化專案） 或.idl 檔案 （非屬性化專案）。|
   |**必要**|指定的物件可能，也可能不是藉由新增元件的屬性巨集 custom(TLBATTR_TRANS_REQUIRED,0).h 檔 （屬性化專案） 或.idl 檔案 （非屬性化專案） 的交易資料流的根目錄。|
   |**不支援**|指定物件排除的交易。 .H 檔 （屬性化專案） 或.idl 檔案 （非屬性化專案），請加入 元件屬性巨集 custom(TLBATTR_TRANS_NOTSUPP,0)。|
   |**必須是新交易**|指定物件一律交易資料流的根目錄加入元件的屬性巨集 custom(TLBATTR_TRANS_REQNEW,0).h 檔 （屬性化專案） 或.idl 檔案 （非屬性化專案）。|

## <a name="see-also"></a>另請參閱

[ATL COM+ 1.0 元件精靈](../../atl/reference/atl-com-plus-1-0-component-wizard.md)<br/>
[ATL COM + 1.0 元件](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

