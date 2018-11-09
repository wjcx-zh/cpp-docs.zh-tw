---
title: 加入成員函式精靈
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.function.overview
helpviewer_keywords:
- Add Member Function Wizard [C++]
ms.assetid: 13b6defc-faa6-4d57-83db-9dd854cbea3d
ms.openlocfilehash: 6ba95026d712c71a9d706baddfefda548100c64a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615042"
---
# <a name="add-member-function-wizard"></a>加入成員函式精靈

此精靈會針對所選類別，將成員函式宣告新增至標頭檔，並將虛設常式成員函式實作新增至實作檔。

一旦您使用精靈新增成員函式，就可以在開發環境中編輯程式碼。

- **傳回類型**

   設定您要新增之成員函式的傳回型別。 您可以提供自己的傳回型別，或從可用型別清單中選取。 如需這些型別的資訊，請參閱[基本型別](../cpp/fundamental-types-cpp.md)。

   ||||
   |-|-|-|
   |**char**|**int**|**unsigned int**|
   |**double**|**long**|**unsigned long**|
   |**float**|**short**|**void**|
   |`HRESULT`|**unsigned char**||

- **函式名稱**

   設定您要新增之成員函式的名稱。

- **參數型別**

   如果成員函式有參數，設定您要為成員函式新增的參數型別。 您可以提供自己的參數型別，或從可用型別清單中選取。

   ||||
   |-|-|-|
   |**char**|**int**|**unsigned char**|
   |**double**|**long**|**unsigned int**|
   |**float**|**short**|**unsigned long**|

- **參數名稱**

   如果成員函式有參數，請設定您要為成員函式新增的參數名稱。

- **參數清單**

   顯示您已新增至成員函式的參數清單。 若要將參數新增至清單，請在 [參數類型] 和 [參數名稱] 方塊中提供類型和名稱，然後按一下 [新增]。 若要從清單移除參數，請選取參數，然後按一下 [移除]。

- **存取權**

   設定成員函式的存取權。 存取修飾詞是指定其他類別對成員函式所具有之存取權的關鍵字。 如需指定存取權的詳細資訊，請參閱[成員存取控制](../cpp/member-access-control-cpp.md)。 成員函式存取層級預設為 **public**。

   - [public](../cpp/public-cpp.md)

   - [protected](../cpp/protected-cpp.md)

   - [private](../cpp/private-cpp.md)

   請檢查新的成員函式是靜態還是虛擬，以及它是內嵌還是純虛擬函式。 如果您將成員函式設為純虛擬函式，則會選取 `Virtual` 核取方塊，且 [內嵌] 核取方塊會變成無法使用。 預設為非靜態、非虛擬成員函式。

   |選項|描述|
   |------------|-----------------|
   |[Static](../cpp/storage-classes-cpp.md)|指定函式的作用就像全域而且可以在類別以外呼叫，即使沒有類別具現化。 成員函式無法存取非靜態成員。 指定為 `Static` 的成員函式不可為虛擬。|
   |[虛擬](../cpp/virtual-cpp.md)|不論呼叫成員函式時使用的運算式為何，都可確保針對物件呼叫正確的成員函式。 指定為 `Virtual` 的成員函式不可為靜態。|
   |**純虛擬**|表示沒有提供實作給正在宣告的虛擬成員函式；因此，只能在虛擬成員函式上指定 [純虛擬]。 至少包含一個純虛擬成員函式的類別會被視為抽象類別。 衍生自抽象類別的類別必須實作純虛擬成員函式，否則這些類別也是抽象類別。|
   |[內嵌](../cpp/inline-functions-cpp.md)|指示編譯器插入份成員函式主體複本至呼叫成員函式的每個地方。 指定為**內嵌**的成員函式不可為純虛擬。|

- **.cpp 檔**

   設定寫入虛設常式成員函式實作的檔案位置。 根據預設，它會寫入至新增成員函式類別的 .cpp 檔。 按一下省略符號按鈕，以變更檔案名稱。 成員函式實作會新增至所選取檔案的內容。

- **註解**

   提供成員函式之標頭檔中的註解。

- **函式簽章**

   當您按一下 [完成] 時，顯示出現在程式碼中的成員函式。 您無法編輯此方塊中的文字。 若要變更成員函式，請變更精靈中的適當方塊。

## <a name="see-also"></a>請參閱

[新增成員函式](../ide/adding-a-member-function-visual-cpp.md)