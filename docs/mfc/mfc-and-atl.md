---
title: MFC 和 ATL |Microsoft 文件
ms.custom: ''
ms.date: 01/24/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 31b1a3a8-4154-4c4a-af10-fafc23ecdc5c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 081414d3835a8a6efcc831b6c303b774361b743b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347730"
---
# <a name="mfc-and-atl"></a>MFC 和 ATL
Microsoft Foundation Classes (MFC) 透過 Win32 提供 C++ 物件導向包裝函式，以便快速開發原生桌面應用程式。 Active Template Library (ATL) 是簡化 COM 開發，並且廣泛用於建立 ActiveX 控制項的包裝函式程式庫。  
  
您可以使用 Visual Studio Community Edition 或更新版本建立 MFC 或 ATL 程式。 Express Edition 不支援 MFC 或 ATL。 

在 Visual Studio 2015 中，Visual C++ 是選用元件，而 MFC 和 ATL 元件是 Visual C++ 底下的選用子元件。 如果您第一次安裝 Visual Studio 時未選取這些元件，當您第一次嘗試建立或開啟 MFC 或 ATL 專案時，系統會提示您安裝這些元件。  

在 Visual Studio 2017 和更新版本，MFC 和 ATL 是底下的選用子元件**的 c + + 桌面應用程式開發**Visual Studio 安裝程式中的工作負載。 您可以安裝 ATL 支援，而非 MFC，或結合 MFC 和 ATL 支援 （MFC 取決於 ATL）。 如需有關工作負載和元件的詳細資訊，請參閱[安裝 Visual Studio 2017](/visualstudio/install/install-visual-studio)。
  
## <a name="related-articles"></a>相關文章  
  
|標題|描述|  
|-----------|-----------------|  
|[MFC 傳統型應用程式](../mfc/mfc-desktop-applications.md)|Microsoft Foundation Classes 透過 Win32 提供精簡型物件導向包裝函式，以便在 C++ 中快速開發 GUI 應用程式。|  
|[ATL COM 桌面元件](../atl/atl-com-desktop-components.md)|ATL 提供類別樣板及其他用途建構，以簡化 C++ 中的 COM 物件建立作業。|  
|[ATL/MFC 共用類別](../atl-mfc-shared/atl-mfc-shared-classes.md)|由 MFC 和 ATL 共用之 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md) 和其他類別的參考。|  
|[使用資源檔](../windows/working-with-resource-files.md)|資源編輯器可讓您編輯 UI 資源，例如字串、影像及對話方塊。|  
|[Visual C++](../visual-cpp-in-visual-studio.md)|MSDN Library 中所有 C++ 內容的父主題。|