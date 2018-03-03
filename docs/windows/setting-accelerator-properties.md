---
title: "設定快速鍵屬性 |Microsoft 文件"
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
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 83eea84c89a9f9873b687333b7454d9f3c9c41b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="setting-accelerator-properties"></a>設定快速鍵屬性
您可以在設定快速鍵屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)在任何時間。 您也可以使用快速鍵編輯器來修改快速鍵對應表中的快速鍵屬性。 使用 [屬性] 視窗或快速鍵編輯器所做的變更會有相同的結果：編輯會立即反映在快速鍵對應表中。  
  
 有三個屬性，每個 accelerator[識別碼](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/3487f185-de96-4b1d-87db-034a52223160/locales/en-US):  
  
-   [Modifier 屬性](../windows/accelerator-modifier-property.md)設定控制項的快速鍵組合。  
  
    > [!NOTE]
    >  在 [屬性] 視窗中，這個屬性會顯示為三個不同的布林值屬性，且三個屬性都可以獨立控制：Alt、Ctrl 和 Shift 鍵。  
  
-   [的索引鍵屬性](../windows/accelerator-key-property.md)設定做為快速鍵的實際索引鍵。  
  
-   [型別屬性](../windows/accelerator-type-property.md)決定索引鍵是否會解譯為虛擬 (VIRTKEY) 或 ASCII/ANSI。  
  

  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [預先定義的快速鍵](../windows/predefined-accelerator-keys.md)   
 [資源編輯器](../windows/resource-editors.md)   
 [快速鍵編輯器](../windows/accelerator-editor.md)