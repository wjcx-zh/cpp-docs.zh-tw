---
title: "符號值限制 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.symbol.restrictions.value
dev_langs:
- C++
helpviewer_keywords:
- symbols, value restrictions
- restrictions, symbol values
ms.assetid: 32467ec3-690b-4cd0-a4d0-7d189a3296cb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5f2188d6904274fabce0f8626fa2f440ac324ff5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="symbol-value-restrictions"></a>符號值限制
符號值可以是針對 #define 前置處理器指示詞以正常方式表示的任何整數。 以下是符號值的一些範例：  
  
```  
18  
4001  
0x0012  
-3456  
```  
  
 資源 (加速器、點陣圖、游標、對話方塊、圖示、功能表、字串資料表及版本資訊) 的符號值必須是介於 0 到 32767 的十進位數字 (但是不能為十六進位)。 資源組件 (例如對話方塊控制項或字串資料表中的個別字串) 的符號值可以從 0 到 65,534 或從 -32,768 到 32,767。  
  
 資源符號是 16 位元數字。 您可以帶正負號或不帶正負號輸入它們，不過，它們在內部是做為不帶正負號整數使用。 因此負數會轉換成對應的正數。  
  
 以下是符號值的一些限制：  
  
-   Visual Studio 開發環境和 MFC 將一些數字範圍用於特殊用途。 MFC 會保留最大顯著性位元的所有數字 (-32,768 到 -1 或 32,768 到 65,534，根據正負號)。  
  
-   您無法使用其他符號字串定義符號值。 例如，不支援下列符號定義：  
  
    ```  
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported  
    ```  
  
-   您無法使用具有引數的前置處理器巨集做為值定義。 例如:   
  
    ```  
    #define   IDD_ABOUT  ID(7) //not supported  
    ```  
  
     不是有效的運算式，無論在編譯階段 `ID` 評估為何種項目。  
  
-   您的應用程式可能具有現有檔案，包含以運算式定義的符號。 如需有關如何納入符號做為唯讀符號的詳細資訊，請參閱[使用共用 （唯讀） 或計算符號](../windows/including-shared-read-only-or-calculated-symbols.md)。  
  
 如需有關數字範圍的詳細資訊，請參閱[TN023： 標準 MFC 資源](../mfc/tn023-standard-mfc-resources.md)。  
  

  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [變更符號的數值](../windows/changing-a-symbol-s-numeric-value.md)   
 [符號名稱限制](../windows/symbol-name-restrictions.md)   
 [預先定義的符號識別碼](../windows/predefined-symbol-ids.md)