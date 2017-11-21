---
title: "樹狀目錄控制項影像清單 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0b4864f4ac15a1d07deb4c3cb8a8d533b8cc4b82
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="tree-control-image-lists"></a>樹狀目錄控制項影像清單
樹狀結構控制項中的每個項目 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 可以有一組與其相關聯的點陣圖影像。 項目的標籤左邊顯示的影像。 當選取的項目，並不選取項目顯示的其他時，會顯示一個影像。 例如，項目可能會顯示開啟的資料夾，選取時，關閉的資料夾時未選取。  
  
 若要使用項目影像，您必須建立影像清單建構[CImageList](../mfc/reference/cimagelist-class.md)物件並使用[CImageList::Create](../mfc/reference/cimagelist-class.md#create)函式來建立關聯的影像清單。 然後將所需的點陣圖新增至清單中，並使用與樹狀目錄控制項相關聯清單[SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist)成員函式。 根據預設，所有項目會顯示在選取及未選取狀態的影像清單中的第一個影像。 您可以變更特定項目的預設行為，藉由指定的選取和未選取映像的索引時將項目加入樹狀目錄控制項使用[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)成員函式。 您可以藉由加入項目之後變更索引[SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage)成員函式。  
  
 樹狀目錄控制項影像清單也可以包含專為會重疊項目影像上的覆疊影像。 中的樹狀目錄控制項目狀態的位元 8 到 11 則為非零值，指定的其中一個基礎覆疊影像的索引 （0 表示無覆疊影像）。 使用 4 位元，1 為基底的索引，因為覆疊影像必須是影像清單中的前 15 映像。 如需有關樹狀目錄控制項目狀態的詳細資訊，請參閱[樹狀目錄控制項項目狀態概觀](../mfc/tree-control-item-states-overview.md)稍早在本主題。  
  
 如果指定了狀態映像清單時，樹狀目錄控制項就會保留狀態影像的每個項目圖示左邊的空間。 應用程式可以使用狀態的影像，例如核取或清除核取方塊，以指出應用程式定義的項目狀態。 非零的值，以位元 12 至 15 指定 1 為基底的索引狀態影像 （0 表示無狀態影像）。  
  
 藉由指定**I_IMAGECALLBACK**值而不是影像的索引，您可以延遲重新繪製項目之前，請指定選取或未選取的映像。 **I_IMAGECALLBACK**指示樹狀目錄控制項來查詢索引的應用程式傳送[TVN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518)通知訊息。  
  
 [GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist)成員函式會擷取樹狀目錄控制項影像清單控制代碼。 此函式是您需要將更多的影像加入至清單時相當實用。 如需影像清單的詳細資訊，請參閱[使用 CImageList](../mfc/using-cimagelist.md)， [CImageList](../mfc/reference/cimagelist-class.md)中*MFC 參考*，和[影像清單](http://msdn.microsoft.com/library/windows/desktop/bb761389)中Windows SDK。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)

