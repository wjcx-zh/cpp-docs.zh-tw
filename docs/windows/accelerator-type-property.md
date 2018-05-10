---
title: 快速鍵類型屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cb1ba8f117fadab7cccb835ba8889d57bcc9f184
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="accelerator-type-property"></a>快速鍵類型屬性
快速鍵**類型**屬性決定快速鍵 ID 相關聯的快速鍵組合是虛擬的按鍵組合或 ASCII/ANSI 機碼值：  
  
-   如果**類型**屬性是**ASCII**、[修飾詞](../windows/accelerator-modifier-property.md)只能是無或 alt 鍵，也可以有使用 CTRL 鍵加速器 (之前的金鑰指定 ^)。  
  
-   如果**類型**屬性是**VIRTKEY**，輔助按鍵和按鍵值的任何組合都有效。  
  
    > [!NOTE]
    >  如果您想要快速鍵對應表中輸入值，而且有被視為 ASCII/ANSI 值，只要按一下資料表中的項目類型，從下拉式清單中的選取 ASCII。 不過，如果您使用**下一個輸入的索引鍵**命令 (**編輯**功能表) 指定的索引鍵，您必須變更**類型**屬性從 VIRTKEY ASCII *之前*輸入按鍵碼。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [設定快速鍵屬性](../windows/setting-accelerator-properties.md)   
 [快速鍵編輯器](../windows/accelerator-editor.md)