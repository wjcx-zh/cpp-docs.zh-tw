---
title: "哪些 ATL 類別簡化 ActiveX 控制項內含項目？ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
ms.assetid: 803a4605-7f4c-4139-8638-49d8783d31b0
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0346f362dac7a184691feac4a8dab25f5709e095
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="which-atl-classes-facilitate-activex-control-containment"></a>哪些 ATL 類別簡化 ActiveX 控制項內含項目？
ATL 的控制項裝載程式碼不需要您使用任何 ATL 類別。您可以直接建立**"AtlAxWin80"**視窗並使用必要的控制項裝載 API (如需詳細資訊，請參閱**為何，ATL 控制項裝載 API**。 不過，下列類別簡化內含項目功能使用。  
  
|類別|說明|  
|-----------|-----------------|  
|[CAxWindow](../atl/reference/caxwindow-class.md)|包裝**"AtlAxWin80"**視窗中，提供方法，來建立視窗、 建立控制項及/或附加控制項視窗中，並擷取主機物件上的介面指標。|  
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|包裝**"AtlAxWinLic80"**視窗中，提供方法，來建立視窗、 建立控制項及/或附加授權的控制項至視窗，並擷取主機物件上的介面指標。|  
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|做為對話方塊資源為基礎的 ActiveX 控制項類別的基底類別。 這類控制項可以包含其他 ActiveX 控制項。|  
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|做為根據的對話方塊資源的對話方塊類別的基底類別。 這類對話方塊可以包含 ActiveX 控制項。|  
|[CWindow](../atl/reference/cwindow-class.md)|提供一種方法， [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol)，這會傳回介面指標上的控制項，指定其裝載視窗的識別碼。 此外，Windows 應用程式開發介面包裝函式會由`CWindow`通常讓視窗管理更輕鬆。|  
  
## <a name="see-also"></a>另請參閱  
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)

