---
title: 快速鍵按鍵屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Key property
ms.assetid: d1570cd9-b414-4cd6-96bd-47c38281eaca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e4fc56384d666026f4cc7e21f9d8af9347046fd1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="accelerator-key-property"></a>快速鍵按鍵屬性
以下是合法的快速鍵對應表中的索引鍵屬性的項目：  
  
-   介於 0 到 255 的十進位整數。 值會決定是否值會被視為 ASCII 或 ANSI，如下所示：  
  
    -   單一位數的數字會解譯為對應的索引鍵，而不是 ASCII 或 ANSI 值。  
  
    -   從 1 到 26 時加上零的值會解譯為 ^ A 到 ^ Z，代表字母時與按下 CTRL 鍵一同按下的 ASCII 值。  
  
    -   27 到 32 之間的值一律解譯為三位數的十進位值 027 032 到。  
  
    -   加上 0 的還是不會被解譯為 ansi 033 到 255 中的值。  
  
-   鍵盤字元。 大寫字母 A-Z 或數字 0-9 可以是 ASCII 或虛擬索引鍵值;任意字元只是 ASCII。  
  
-   鍵盤字元 A-Z 範圍內 （僅有大寫字母） 加上的插入號 (^) (例如 ^ C)。 按住 CTRL 鍵，按下時，這就會進入索引鍵的 ASCII 值。  
  
    > [!NOTE]
    >  輸入 ASCII 值時，輔助按鍵屬性選項將會受到限制。 只有 control 鍵可供使用的是 ALT 鍵。  
  
-   任何有效的虛擬索引鍵識別碼。 快速鍵對應表中的下拉式清單金鑰 方塊包含標準虛擬按鍵識別碼的清單。  
  
    > [!TIP]
    >  另一種方式定義快速鍵是以滑鼠右鍵按一下某個項目或多個項目快速鍵對應表中的，選擇 **下一個輸入的索引鍵**從捷徑功能表，然後在鍵盤上按任一按鍵或按鍵組合。 **下一個輸入的索引鍵**命令也會提供**編輯**功能表。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [設定快速鍵屬性](../windows/setting-accelerator-properties.md)   
 [編輯快速鍵對應表中](../windows/editing-in-an-accelerator-table.md)   
 [快速鍵編輯器](../windows/accelerator-editor.md)