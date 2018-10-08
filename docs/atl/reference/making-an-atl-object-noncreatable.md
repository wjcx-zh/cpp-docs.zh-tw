---
title: 讓 ATL 物件變成無法建立 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.objects
dev_langs:
- C++
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0b20cbae3036ffecfa63f2e3ee6be8e2153fc8f
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860910"
---
# <a name="making-an-atl-object-noncreatable"></a>讓 ATL 物件變成無法建立

您可以變更 COM 物件的屬性，讓用戶端無法直接建立物件。 在此情況下，該物件會是透過方法呼叫所傳回的另一個物件而非直接建立。

## <a name="to-make-an-object-noncreatable"></a>若要讓物件變成無法建立

1. 移除[OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto)物件。 如果您想要會變成無法建立，但註冊控制項的物件，取代使用 OBJECT_ENTRY_AUTO [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)。

1. 新增[noncreatable](../../windows/noncreatable.md) .idl 檔案中 coclass 的屬性。 例如: 

    ```  
    [uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851), 
    helpstring("MyObject"), 
    noncreatable]  
    coclass MyObject  
    {  
        [default] interface IMyInterface;  
    }  
    ```

## <a name="see-also"></a>另請參閱

[ATL 專案精靈](../../atl/reference/atl-project-wizard.md)<br/>
[Visual C++ 專案類型](../../ide/visual-cpp-project-types.md)<br/>
[使用應用程式精靈建立桌面專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[使用 ATL 和 C 執行階段程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[預設 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)
