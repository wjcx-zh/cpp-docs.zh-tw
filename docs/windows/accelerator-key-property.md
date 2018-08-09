---
title: 快速鍵按鍵屬性 |Microsoft Docs
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
ms.openlocfilehash: 36884376e5ff31754e4c53ef6602f6bfd129f4a4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650439"
---
# <a name="accelerator-key-property"></a>快速鍵按鍵屬性
以下是合法的快速鍵對應表中的索引鍵屬性的項目：  
  
-   介於 0 到 255 的十進位整數。 值會決定是否此值會被視為 ASCII 或 ANSI，如下所示：  
  
    -   單一位數的數字一律會解譯為相對應的索引鍵，而不是 ASCII 或 ANSI 值。  
  
    -   從 1 到 26，前面加零上時的值會解譯為 ^ A 到 ^ Z，代表字母表的字母與按下時的 ASCII 值**Ctrl**按住按鍵。  
  
    -   27 到 32 之間的值一律解譯為三位數十進位值 027 032 到。  
  
    -   加上 0，還是不會被解譯為 ANSI 值從 033 到 255 之間的數值。  
  
-   鍵盤字元。 大寫 A-Z 或數字 0-9 可以是 ASCII 或虛擬索引鍵值;任何其他字元只為 ASCII。  
  
-   鍵盤字元 A – Z 範圍內 （僅有大寫） 加上插入號 (^) (例如，^ C)。 這會進入索引鍵的 ASCII 值，與按下時**Ctrl**按住按鍵。  
  
    > [!NOTE]
    >  時輸入 ASCII 值，輔助按鍵屬性選項將會受到限制。 是唯一可用的控制鍵使用**Alt**索引鍵。  
  
-   任何有效的虛擬索引鍵識別碼。 快速鍵對應表中的 [下拉式清單金鑰] 方塊包含一份標準的虛擬索引鍵識別碼。  
  
    > [!TIP]
    >  定義快速鍵的另一個方法是以滑鼠右鍵按一下某個項目或快速鍵對應表中的多個項目，請選擇**下一步 輸入的按鍵**從捷徑功能表，然後在鍵盤上按任何按鍵或按鍵組合。 **下一步 輸入的按鍵**命令也會提供**編輯**功能表。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [設定快速鍵屬性](../windows/setting-accelerator-properties.md)   
 [在快速鍵對應表中編輯](../windows/editing-in-an-accelerator-table.md)   
 [快速鍵編輯器](../windows/accelerator-editor.md)