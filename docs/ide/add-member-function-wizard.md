---
title: "加入成員函式精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.function.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "加入成員函式精靈 [C++]"
ms.assetid: 13b6defc-faa6-4d57-83db-9dd854cbea3d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 加入成員函式精靈
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個精靈將一個成員函式宣告加入至標頭檔並將一個 Stub 成員函式實作 \(Implementation\) 加入至所選取類別的實作檔中。  
  
 一旦您使用精靈加入了成員函式，您就可以在開發環境中編輯其程式碼。  
  
 **傳回型別**  
 設定所加入成員函式的傳回型別。  您可以提供自訂的傳回型別，或從可用的型別清單中選取。  如需有關型別的資訊，請參閱[主要資料型別](../cpp/fundamental-types-cpp.md) \(Fundamental Type\)。  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned int`|  
|**double**|**long**|`unsigned long`|  
|**float**|**short**|`void`|  
|`HRESULT`|`unsigned char`||  
  
 **函式名稱**  
 設定加入之成員函式的名稱。  
  
 **參數型別**  
 設定加入之成員函式參數的型別，若該成員函式具有參數。  您可以提供您自己的參數型別，或者您可以從可用的型別清單中選取。  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned char`|  
|**double**|**long**|`unsigned int`|  
|**float**|**short**|`unsigned long`|  
  
 **參數名稱**  
 設定加入之成員函式參數的名稱，若該成員函式具有參數。  
  
 **參數清單**  
 顯示加入之成員函式參數的清單。  若要將參數加入清單，請分別在 \[參數型別\] 和 \[參數名稱\] 對話方塊提供一個型別和名稱，然後按一下 \[加入\]。  若要將參數從清單移除，請選取該參數再按一下 \[移除\]。  
  
 **存取權**  
 設定對成員函式的存取。  存取修飾詞 \(Modifier\) 是指定其他型別對成員函式之存取的關鍵字。  如需關於指定存取的詳細資訊，請參閱[成員存取控制](../cpp/member-access-control-cpp.md) \(Member\-Access Control\)。  成員函式的存取層次預設為 **public**。  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
 檢查新的成員函式為 Static 或 Virtual，以及 Inline 或 Pure。  如果您將成員函式設定為 Pure，則 \[`Virtual`\] 核取方塊也被選取，而 \[Inline\] 核取方塊則變成無法使用。  預設值是非 Static、非 Virtual 的成員函式。  
  
|選項|描述|  
|--------|--------|  
|[Static](../misc/static-cpp.md)|指定函式如同全域函式一般可以從類別外呼叫，即使沒有類別執行個體化 \(Instantiation\)。  成員函式不能存取非靜態成員。  被指定為 `Static` 的成員函式不可為 Virtual。|  
|[虛擬](../cpp/virtual-cpp.md)|確保物件呼叫的是正確的成員函式，不論呼叫成員函式時使用的運算式。  被指定為 `Virtual` 的成員函式不可為 Static。|  
|**Pure**|表示對所宣告的 Virtual 成員函式沒有提供實作；因此，**Pure** 只能指定 Virtual 成員函式。  如需詳細資訊，請參閱[類別成員宣告語法](../misc/class-member-declaration-syntax.md)。<br /><br /> 包含至少一個純虛擬成員函式的類別被視為一個抽象類別 \(Abstract Class\)。  由抽象類別衍生出來的類別必須實作純虛擬成員函式，否則它們也是抽象類別。|  
|[內嵌](../cpp/inline-functions-cpp.md)|指示編譯器 \(Compiler\) 在每個呼叫成員函式的位置插入一份成員函式主體。  被指定為 **Inline** 的成員函式不可為純粹。|  
  
 **.cpp 檔**  
 設定檔案 Stub 成員函式實作寫入的位置。  依照預設，它是被寫入加入成員函式的類別的 .cpp 檔中。  按一下 \[省略\] 按鈕以變更檔案名稱。  成員函式的實作會被加入選取檔案的內容中。  
  
 **註解**  
 提供標頭檔中成員函式的註解。  
  
 **函式簽章**  
 顯示當您按一下 \[完成\] 按鈕時出現於程式碼中的成員函式。  您不能編輯這個方塊裡的文字。  若要變更成員函式，請變更精靈中適當的方塊。  
  
## 請參閱  
 [加入成員函式](../ide/adding-a-member-function-visual-cpp.md)