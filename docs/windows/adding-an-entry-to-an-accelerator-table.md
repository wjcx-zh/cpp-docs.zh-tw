---
title: 快速鍵對應表中加入項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], adding entries
- New Accelerator command
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 22f3e00c8ba6523f6cc615e4a766ad9206560b5e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33855366"
---
# <a name="adding-an-entry-to-an-accelerator-table"></a>在快速鍵對應表中加入項目
### <a name="to-add-an-entry-to-an-accelerator-table"></a>在快速鍵對應表中加入項目  
  
1.  它在圖示上按兩下開啟快速鍵對應表[資源檢視](../windows/resource-view-window.md)。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  快速鍵對應表內按一下滑鼠右鍵，然後選擇 **新增快速鍵**從捷徑功能表或按一下空白資料列項目底部的資料表。  
  
3.  選取[識別碼](id-property.md)從識別碼中的下拉式清單方塊，或輸入新的識別碼在**識別碼**方塊。  
  
4.  型別[金鑰](../windows/accelerator-key-property.md)您想要做為快速鍵或以滑鼠右鍵按一下，然後選擇 **下一個輸入的索引鍵**從捷徑功能表，來設定按鍵組合 (**下一個輸入的索引鍵**命令也可從**編輯**功能表)。  
  
5.  變更[修飾詞](../windows/accelerator-modifier-property.md)和[類型](../windows/accelerator-type-property.md)，必要時。  
  
6.  按 **ENTER** 鍵。  
  
    > [!NOTE]
    >  確定定義的所有快速鍵都是唯一的。 您可以有數個按鍵組合，指派給相同的 ID 而不會有不良影響，例如，CTRL + P 和 F8 可以同時指派給 ID_PRINT。 不過，將一個按鍵組合指派給多個 ID 將無法運作，例如，將 CTRL + Z 指派給 ID_SPELL_CHECK 和 ID_THESAURUS。  
  

  
 **需求**  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [編輯快速鍵對應表](../windows/editing-accelerator-tables.md)   
 [快速鍵編輯器](../windows/accelerator-editor.md)