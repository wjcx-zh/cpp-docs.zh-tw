---
title: "快速鍵輔助按鍵屬性 |Microsoft 文件"
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
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 63d6a4b526fc1f2aeb2a942e682a8c7cc6f9b58c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="accelerator-modifier-property"></a>快速鍵輔助按鍵屬性
以下是合法的快速鍵對應表中的修飾詞屬性的項目。  
  
|值|描述|  
|-----------|-----------------|  
|**無**|使用者按下按鍵值。 這最有效地用於 ASCII/ANSI 值 001 026，透過可解譯為 ^ A 到 ^ Z (CTRL-透過 CTRL-Z 的 A)。|  
|**Alt 鍵**|使用者必須按下 ALT 鍵之前的金鑰值。|  
|**Ctrl**|使用者必須按下 CTRL 鍵之前的金鑰值。 ASCII 類型不正確。|  
|**Shift 鍵**|使用者必須按 SHIFT 鍵之前的金鑰值。|  
|**Ctrl + Alt**|使用者必須按下 CTRL 鍵和 ALT 鍵之前的金鑰值。 ASCII 類型不正確。|  
|**Ctrl + shift 鍵**|使用者必須按下 CTRL 鍵和 SHIFT 鍵之前的金鑰值。 ASCII 類型不正確。|  
|**Alt + Shift**|使用者必須按下 ALT 鍵和 SHIFT 鍵之前的金鑰值。 ASCII 類型不正確。|  
|**Ctrl + Alt + Shift**|使用者必須按 CTRL、 ALT 和 SHIFT 之前的金鑰值。 ASCII 類型不正確。|  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [設定快速鍵屬性](../windows/setting-accelerator-properties.md)   
 [快速鍵編輯器](../windows/accelerator-editor.md)