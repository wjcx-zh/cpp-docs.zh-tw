---
title: "範本 ref 類別 (C + + /CX) |Microsoft 文件"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a24d5f45-8dbb-4540-958f-c76c90d8ed93
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f135907a4aba473db62734f9370ee82b7113c66d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="template-ref-classes-ccx"></a>範本 ref 類別 (C++/CX)
C++ 範本不會發行到中繼資料，因此，在您的程式中不能有公用或受保護存取範圍。 當然，您可以在內部自己的程式中使用 Standard C++ 範本。 此外，您可以將私用 ref 類別定義為樣板，並可以將明確特製化的樣板 ref 類別宣告為公用 ref 類別的私用成員。  
  
## <a name="authoring-ref-class-templates"></a>撰寫 ref 類別樣板  
 下列範例示範如何將私用 ref 類別宣告為樣板，也會示範如何宣告 Standard C++ 範本，以及如何將這兩個樣板同時宣告為公用 ref 類別的成員。 請注意，可以標準 c + + 樣板特製化，由 Windows 執行階段型別，在此情況下 platform:: string ^。  
  
 [!code-cpp[cx_templates#01](../cppcx/codesnippet/CPP/templatedemo/class1.h#01)]  
  
## <a name="see-also"></a>請參閱  
 [類型系統 (C++/CX)](../cppcx/type-system-c-cx.md)   
 [Visual c + + 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)