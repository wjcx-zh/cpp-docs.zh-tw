---
title: 屬性 (C + + /CX) |Microsoft 文件
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 64c7bc56-3191-4cd5-bdf4-476d07d285d5
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6393b5e5849ab2198fa8d084c2c1d15838c69bdd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089555"
---
# <a name="properties-ccx"></a>屬性 (C++/CX)
Windows 執行階段類型將公用資料公開為屬性。 用戶端程式碼可將此屬性視為公用 Datamember 加以存取。 此屬性在內部可實作為包含 get 存取子方法和 (或) set 存取子方法的區塊。 使用存取子方法，可讓您在擷取值之前或之後執行其他動作，例如，您可以引發事件或執行驗證檢查。  
  
### <a name="remarks"></a>備註  
 屬性的值包含於私用變數中，稱為「 *備份存放區*」(Backing Store)，其型别與屬性相同。 一個屬性可同時包含 set 存取子與 get 存取子，前者可指派值給備份存放區，後者則可擷取備份存放區的值。 若僅提供 get 存取子，則是唯讀屬性，若僅提供 set 存取子，則是唯寫屬性，若兩種存取子皆提供，則是讀/寫 (可修改) 屬性。  
  
 *trivial* 屬性屬於編譯器會自動實作存取子和備份存放區的讀/寫屬性。 您無法存取編譯器的實作。 但是，您可以宣告自訂屬性，並明確宣告其存取子和備份存放區。 在存取子中，您可以執行任何您所需的邏輯，例如驗證 set 存取子的輸入、計算屬性值的值、存取資料庫，或在屬性變更時引發事件。  
  
 具現化 C++/CX ref 類別時，會在呼叫其建構函式之前，將其記憶體初始設定為零；因此，會在宣告時將預設值 0 或 nullptr 指派給所有屬性。  
  
### <a name="examples"></a>範例  
 下列程式碼範例說明如何宣告及存取屬性。 第一個屬性 `Name`稱為 *trivial* 屬性，因為編譯器會自動產生 `set` 存取子、 `get` 存取子與備份存放區。  
  
 第二個屬性 `Doctor`是唯讀屬性，因為它會指定只明確宣告 *存取子的* 屬性區塊 `get` 。 由於已宣告 Property 區塊，因此您必須明確宣告備份存放區，即私用 String^ 變數 `doctor_`。 一般而言，唯讀屬性只會傳回備份存放區的值。 只有類別本身可以設定備份存放區的值，通常在建構函式中。  
  
 第三個屬性 `Quantity`是讀/寫屬性，因為它會宣告可同時宣告 `set` 存取子和 `get` 存取子的 Property 區塊。  
  
 `set` 存取子會對指派的值執行使用者定義的有效性測試。 此外，不同於 C#，此處的名稱 *value* 只是 `set` 存取子中參數的識別項，而不是關鍵字。 如果 *value* 不大於零，則會擲回 Platform::InvalidArgumentException。 若大於零，則會以指派的值更新備份存放區 `quantity_`。  
  
 請注意，屬性無法在成員清單中初始化。 您當然可以在成員清單中初始化備份存放區變數。  
  
 [!code-cpp[cx_properties#01](../cppcx/codesnippet/CPP/cx_properties/class1.h#01)]  
  
## <a name="see-also"></a>另請參閱  
 [類型系統](../cppcx/type-system-c-cx.md)   
 [Visual c + + 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)