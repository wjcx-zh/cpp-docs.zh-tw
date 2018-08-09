---
title: 快速鍵輔助按鍵屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0788536e776661b9a84a6cccc648a7db68389ae5
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644251"
---
# <a name="accelerator-modifier-property"></a>快速鍵輔助按鍵屬性
以下是合法的項目快速鍵對應表中的修飾詞 屬性。  
  
|值|描述|  
|-----------|-----------------|  
|**無**|只有使用者按下**金鑰**值。 這最有效地用於 ASCII/ANSI 值 001 026，透過它被解譯為 ^ A 到 ^ Z (CTRL-透過 CTRL-Z 的 A)。|  
|**Alt**|使用者必須按下**Alt**金鑰之前**金鑰**值。|  
|**Ctrl**|使用者必須按下**Ctrl**金鑰之前**金鑰**值。 ASCII 類型無效。|  
|**Shift**|使用者必須按下**Shift**金鑰之前**金鑰**值。|  
|**Ctrl + Alt**|使用者必須按下**Ctrl**機碼並**Alt**金鑰之前**金鑰**值。 ASCII 類型無效。|  
|**Ctrl + shift 鍵**|使用者必須按下**Ctrl**機碼並**Shift**金鑰之前**金鑰**值。 ASCII 類型無效。|  
|**Alt + Shift**|使用者必須按下**Alt**機碼並**Shift**金鑰之前**金鑰**值。 ASCII 類型無效。|  
|**Ctrl + Alt + Shift**|使用者必須按下**Ctrl**， **Alt**，並**Shift**之前**金鑰**值。 ASCII 類型無效。|  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [設定快速鍵屬性](../windows/setting-accelerator-properties.md)   
 [快速鍵編輯器](../windows/accelerator-editor.md)