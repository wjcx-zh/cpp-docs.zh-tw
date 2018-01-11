---
title: "快速鍵類型屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 214d8ca9c45a3657215833764268794b152bd337
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="accelerator-type-property"></a>快速鍵類型屬性
快速鍵**類型**屬性決定快速鍵 ID 相關聯的快速鍵組合是虛擬的按鍵組合或 ASCII/ANSI 機碼值：  
  
-   如果**類型**屬性是**ASCII**、[修飾詞](../windows/accelerator-modifier-property.md)只能是無或 alt 鍵，也可以有使用 CTRL 鍵加速器 (之前的金鑰指定 ^)。  
  
-   如果**類型**屬性是**VIRTKEY**，輔助按鍵和按鍵值的任何組合都有效。  
  
    > [!NOTE]
    >  如果您想要快速鍵對應表中輸入值，而且有被視為 ASCII/ANSI 值，只要按一下資料表中的項目類型，從下拉式清單中的選取 ASCII。 不過，如果您使用**下一個輸入的索引鍵**命令 (**編輯**功能表) 指定的索引鍵，您必須變更**類型**屬性從 VIRTKEY ASCII *之前*輸入按鍵碼。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [設定快速鍵屬性](../windows/setting-accelerator-properties.md)   
 [快速鍵編輯器](../windows/accelerator-editor.md)