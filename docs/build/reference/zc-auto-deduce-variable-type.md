---
title: "-Zc: auto （推算變數類型） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Zc:auto
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dd2f0ff353e1243685c94da0c28f29e810b2a9ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto (推算變數類型)
**/Zc: auto [-]**編譯器選項會告訴編譯器如何使用[auto 關鍵字](../../cpp/auto-keyword.md)宣告變數。 如果您指定預設選項， **/zc: auto**，編譯器會推算的類型宣告的變數，從其初始化運算式。 如果您指定**/Zc:auto-**，編譯器會自動儲存類別將變數配置。  
  
## <a name="syntax"></a>語法  
  
```  
/Zc:auto[-]  
```  
  
## <a name="remarks"></a>備註  
 C++ 標準為 `auto` 關鍵字定義了原始和修訂的意義。 之前[!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)]，關鍵字會宣告自動儲存類別中的變數; 也就是變數具有區域存留期。 從開始[!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)]，關鍵字會推算變數，以從宣告初始化運算式的型別。 使用**/zc: auto [-]**編譯器選項，以告訴編譯器使用的原始或修訂的意義`auto`關鍵字。  
  
 如果 `auto` 關鍵字的使用與目前編譯器選項衝突，則編譯器會發出適當的診斷訊息。 如需詳細資訊，請參閱[auto 關鍵字](../../cpp/auto-keyword.md)。 如需 Visual c + + 一致性問題的詳細資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。  
  
### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**組態屬性**節點。  
  
3.  按一下**C/c + +**節點。  
  
4.  按一下**命令列**節點。  
  
5.  新增**/zc: auto**或**/Zc:auto-**至**其他選項：**窗格。  
  
## <a name="see-also"></a>請參閱  
 [/Zc （一致性）](../../build/reference/zc-conformance.md)   
 [auto 關鍵字](../../cpp/auto-keyword.md)