---
title: "指定屬性頁 (ATL) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ISpecifyPropertyPages
dev_langs:
- C++
helpviewer_keywords:
- ISpecifyPropertyPages method
- property pages, specifying
ms.assetid: ee8678cf-c708-49ab-b0ad-fc2db31f1ac3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8985499c76a7dc65523a5c2904bcb774a4364d41
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-property-pages"></a>指定屬性頁
當您建立 ActiveX 控制項時，您通常要與屬性頁，可以用來設定控制項的屬性產生關聯。 控制容器使用**ISpecifyPropertyPages**介面，以找出哪些屬性頁面可以用來設定控制項的屬性。 您必須實作此介面上您的控制項。  
  
 若要實作**ISpecifyPropertyPages**使用 ATL，採取下列步驟：  
  
1.  衍生您的類別從[ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md)。  
  
2.  新增的項目**ISpecifyPropertyPages**至類別的 COM 對應。  
  
3.  新增[PROP_PAGE](reference/property-map-macros.md#prop_page)與控制項相關聯的每一頁的屬性對應的項目。  
  
> [!NOTE]
>  產生標準控制項使用時[ATL 控制項精靈](../atl/reference/atl-control-wizard.md)，您只需新增`PROP_PAGE`的屬性對應的項目。 精靈會產生必要的程式碼的其他步驟。  
  
 正常運作的容器將會顯示指定的屬性頁中的順序相同`PROP_PAGE`屬性對應中的項目。 一般而言，您應該放入的一般屬性頁面項目之後的項目在屬性對應中，在自訂頁面，讓使用者看到您的控制項特定頁面第一次。  
  
## <a name="example"></a>範例  
 控制項使用的行事曆的下列類別**ISpecifyPropertyPages**告知容器可以使用自訂日期頁面和 [內建的色彩] 頁面設定其屬性的介面。  
  
 [!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/cpp/specifying-property-pages_1.h)]  
  
## <a name="see-also"></a>請參閱  
 [屬性頁](../atl/atl-com-property-pages.md)   
 [ATLPages 範例](../visual-cpp-samples.md)

