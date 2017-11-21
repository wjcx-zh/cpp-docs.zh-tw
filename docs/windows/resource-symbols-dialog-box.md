---
title: "資源符號對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.resourcesymbols
dev_langs: C++
helpviewer_keywords:
- New Symbol dialog box
- Resource Symbols dialog box
- Change Symbol dialog box
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 23095aba32846a61d4fd61f9910994892e1f5ca1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="resource-symbols-dialog-box"></a>資源符號對話方塊
**資源符號**對話方塊可讓您加入新的資源符號、 變更符號會顯示，或跳到原始程式碼中正在使用中的位置。  
  
 **Name**  
 顯示的符號名稱。 如需詳細資訊，請參閱[符號名稱限制](../windows/symbol-name-restrictions.md)。  
  
 **值**  
 顯示符號的數值。 如需詳細資訊，請參閱[符號值限制](../windows/symbol-value-restrictions.md)。  
  
 **使用中**  
 選取時，指定符號正由一或多個資源使用。 一或多個資源會列在 [使用者] 方塊中。  
  
 **顯示唯讀符號**  
 選取時，顯示唯讀資源。 根據預設，[資源符號] 對話方塊僅顯示您的資源指令碼檔案中可修改的資源，但選取這個選項後，可修改的資源會以粗體文字顯示，而唯讀資源會以純文字顯示。  
  
 **使用**  
 使用在符號清單中選取的符號來顯示一或多個資源。 若要移至編輯器] 中指定的資源，選取 [在資源**被使用**方塊，然後按一下**檢視使用**。 如需詳細資訊，請參閱[開啟指定符號的資源編輯器](../windows/opening-the-resource-editor-for-a-given-symbol.md)。  
  
 **新增**  
 開啟 [新增符號] 對話方塊，可讓您定義名稱，以及新符號資源識別項的值 (如有必要)。 如需詳細資訊，請參閱[建立新的符號](../windows/creating-new-symbols.md)。  
  
 **變更**  
 開啟 [變更符號] 對話方塊，可讓您變更符號的名稱或值。 如果符號用於使用中的控制項或資源，只可以從對應的資源編輯器變更符號。 如需詳細資訊，請參閱[變更未指定的符號](../windows/changing-unassigned-symbols.md)。  
  
 **檢視使用**  
 開啟在對應資源編輯器中含有符號的資源。 如需詳細資訊，請參閱[開啟指定符號的資源編輯器](../windows/opening-the-resource-editor-for-a-given-symbol.md)。  
  

  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [檢視資源符號](../windows/viewing-resource-symbols.md)