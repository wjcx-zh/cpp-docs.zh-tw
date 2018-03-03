---
title: "ATL 和 MFC 所選擇的建議 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 079784f1fed84ae073767a4a0b622d3fdbf7384b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>ATL 和 MFC 所選擇的建議
在開發元件和應用程式時，您可以選擇兩種方法，ATL 和 MFC （Microsoft Foundation 類別程式庫）。  
  
## <a name="using-atl"></a>使用 ATL  
 ATL 是快速且簡單的方式，同時在 c + + 中建立 COM 元件和維護佔空間很小。 若要建立的控制項，如果您不需要的所有內建功能，MFC 會自動提供使用 ATL。  
  
## <a name="using-mfc"></a>使用 MFC  
 MFC 可讓您建立完整的應用程式、 ActiveX 控制項和主動式文件。 如果您已經建立控制項與 MFC，您可能想要在 MFC 中繼續開發。 建立新的控制項時，請考慮使用 ATL，如果您不需要所有 MFC 的內建功能。  
  
## <a name="using-atl-in-an-mfc-project"></a>MFC 專案中使用 ATL  
 您可以加入現有的 MFC 專案中使用 ATL，透過執行精靈的支援。 如需詳細資訊，請參閱[將 ATL 支援加入至 MFC 專案](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。  
  
## <a name="see-also"></a>請參閱  
 [ATL 簡介](../atl/introduction-to-atl.md)

