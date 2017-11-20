---
title: "設定註冊機構程式碼 （只有 c + +） 的靜態連結 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b8eb77bc6f99ab6b7d8ca9d51f1a7a8549d8f0c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>設定靜態連結的註冊機構的程式碼 （只有 c + +）
C + + 用戶端可以建立註冊機構的程式碼的靜態連結。 靜態連結的註冊機構的剖析器會將大約 5 K，加入至發行組建。  
  
 最簡單的方式來設定靜態連結會假設您已指定[DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid)物件的宣告中。 （這是預設的規格使用 ATL）  
  
### <a name="to-create-a-static-link-using-declareregistryresourceid"></a>若要建立使用 DECLARE_REGISTRY_RESOURCEID 靜態連結  
  
1.  指定[/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY`而不是 /D**_ATL_DLL**。  
  
2.  重新編譯。  
  
## <a name="see-also"></a>另請參閱  
 [登錄元件 （登錄器）](../atl/atl-registry-component-registrar.md)

