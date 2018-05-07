---
title: 加入成員函式精靈 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.function.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Member Function Wizard [C++]
ms.assetid: 13b6defc-faa6-4d57-83db-9dd854cbea3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 488c7ca455b267a79b0d2906849596346a191792
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="add-member-function-wizard"></a>加入成員函式精靈
此精靈會將成員函式宣告加入至標頭檔與實作檔以取得所選類別的虛設常式成員函式實作。  
  
 一旦您加入成員函式使用精靈，您可以編輯在開發環境中的程式碼。  
  
 **傳回類型**  
 設定您要加入之成員函式的傳回型別。 您可以提供您自己的傳回型別，或您可以從可用類型清單中選取。 類型的相關資訊，請參閱[基本類型](../cpp/fundamental-types-cpp.md)。  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned int`|  
|**double**|**long**|`unsigned long`|  
|**float**|**short**|`void`|  
|`HRESULT`|`unsigned char`||  
  
 **函式名稱**  
 設定您要加入成員函式的名稱。  
  
 **參數型別**  
 如果此成員函式有參數，請設定您要加入成員函式參數的型別。 您可以提供自己的參數類型，或您可以從可用類型清單中選取。  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned char`|  
|**double**|**long**|`unsigned int`|  
|**float**|**short**|`unsigned long`|  
  
 **參數名稱**  
 如果此成員函式有參數，請設定您要加入成員函式參數的名稱。  
  
 **參數清單**  
 顯示您已加入成員函式的參數清單。 若要將參數加入至清單中，提供型別，並命名**參數型別**和**參數名稱**方塊，然後按一下**新增**。 若要從清單中移除參數，請選取參數，然後按一下**移除**。  
  
 **存取權**  
 成員函式中設定的存取。 存取修飾詞是指定其他類別成員函式所擁有的存取權的關鍵字。 請參閱[成員存取控制](../cpp/member-access-control-cpp.md)如需有關指定存取權。 成員函式的存取層級設為**公用**預設。  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
 請檢查新的成員函式是否為靜態或虛擬，以及它是否內嵌或純。 如果您將成員函式是純`Virtual`選取核取方塊，而**內嵌**核取方塊變得無法使用。 預設為非靜態、 非虛擬成員函式。  
  
|選項|描述|  
|------------|-----------------|  
|[Static](../cpp/storage-classes-cpp.md)|指定函式的作用就像全域的而且呼叫以外的類別，即使有沒有類別具現化。 成員函式的非靜態成員無法存取。 成員函式指定為`Static`不可為虛擬。|  
|[虛擬](../cpp/virtual-cpp.md)|可確保正確的成員函式，會呼叫物件，不論用來進行呼叫成員函式的運算式。 成員函式指定為`Virtual`不可以是靜態。|  
|**純虛擬**|表示沒有實作提供宣告; 的虛擬成員函式因此，**純粹**可以只能在虛擬成員函式上指定。 其中包含至少一個純虛擬成員函式的類別會被視為抽象類別。 衍生自抽象類別的類別必須實作純虛擬成員函式，或它們，也是抽象類別。|  
|[內嵌](../cpp/inline-functions-cpp.md)|指示編譯器插入成員函式會呼叫每個位置中的成員函式主體的複本。 成員函式指定為**內嵌**不可為純方法。|  
  
 **.cpp 檔案中**  
 設定虛設常式成員函式實作所寫入之檔案位置。 根據預設，它會寫入至成員函式加入類別的.cpp 檔。 按一下省略符號按鈕，以變更檔案名稱。 成員函式實作會加入至選取的檔案的內容。  
  
 **註解**  
 提供成員函式的標頭檔中的註解。  
  
 **函式簽章**  
 顯示當您按一下出現在程式碼中的成員函式**完成**。 您無法編輯此方塊中的文字。 若要變更此成員函式，變更適當的方塊中的精靈。  
  
## <a name="see-also"></a>另請參閱  
 [加入成員函式](../ide/adding-a-member-function-visual-cpp.md)