---
title: 設定快速鍵屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d329d902014b3dff6f66fd6e3f1877a3bc70822
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016249"
---
# <a name="setting-accelerator-properties"></a>設定快速鍵屬性
您可以在設定快速鍵屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)在任何時間。 您也可以使用**加速器**編輯器來修改快速鍵對應表中的快速鍵屬性。 所做的變更**屬性** 視窗或**加速器**編輯器有相同的結果： 編輯會立即反映在快速鍵對應表。  
  
 有三個屬性的每個加速器[識別碼](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/3487f185-de96-4b1d-87db-034a52223160):  
  
-   [Modifier 屬性](../windows/accelerator-modifier-property.md)設定控制項的快速鍵組合。  
  
    > [!NOTE]
    >  在 [**屬性**] 視窗中，這個屬性會顯示為三個不同的布林屬性，全部都可以獨立控制： **Alt**， **Ctrl**，和**Shift**。  
  
-   [索引鍵屬性](../windows/accelerator-key-property.md)設定要做為快速鍵的實際金鑰。  
  
-   [型別屬性](../windows/accelerator-type-property.md)判斷是否要將按鍵解譯成虛擬 (VIRTKEY) 或 ASCII/ANSI。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [預先定義的快速鍵](../windows/predefined-accelerator-keys.md)   
 [資源編輯器](../windows/resource-editors.md)   
 [快速鍵編輯器](../windows/accelerator-editor.md)