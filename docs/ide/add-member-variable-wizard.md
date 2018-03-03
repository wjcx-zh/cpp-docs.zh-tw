---
title: "加入成員變數精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.variable.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Member Variable Wizard [C++]
ms.assetid: 73e8fa99-ac1a-42e2-8fc2-4684b9eb6d4d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b909ec7ccd830e088df81ca0b2db8cda133c7a20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="add-member-variable-wizard"></a>加入成員變數精靈
這個精靈將在成員變數宣告加入至標頭檔，並根據的選項，它可以將程式碼加入的.cpp 檔案。 一旦您加入成員變數使用精靈，您可以編輯在開發環境中的程式碼。  
  
 **存取權**  
 您可以設定的存取權的成員變數。 存取修飾詞是指定的成員變數對其他類別的存取權的關鍵字。 請參閱[成員存取控制](../cpp/member-access-control-cpp.md)如需有關指定存取權。 成員變數的存取層級設為**公用**預設。  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
 **變數類型**  
 設定您要加入成員變數的傳回型別。  
  
-   如果您要加入成員變數不是對話方塊的控制項，從可用類型清單中選取。  
  
     類型的相關資訊，請參閱[基本類型](../cpp/fundamental-types-cpp.md)。  
  
    |||  
    |-|-|  
    |`char`|**short**|  
    |**double**|`unsigned char`|  
    |**float**|`unsigned int`|  
    |`int`|`unsigned long`|  
    |**long**||  
  
-   如果您要加入對話方塊控制項的成員變數，此方塊會填入控制項或值傳回的物件類型。 如果您選取**控制項**，然後**變數型別**指定您在選取的控制項的基底類別**控制項 ID**方塊。 對話方塊控制項可以包含值，且您選取**值**，然後**變數型別**指定適當的控制項可以包含的值類型。 請參閱[對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)如需詳細資訊。  
  
     這個值取決於在**控制項 ID**且無法變更。  
  
 **變數名稱**  
 設定您要加入成員變數的名稱。 成員變數通常開頭為"m_"的預設會為您提供的識別字串。  
  
 **控制變數**  
 表示成員變數管理內包含的對話方塊控制項[資料交換和驗證資料](../mfc/dialog-data-exchange-and-validation.md)支援。 請參閱[DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)如需詳細資訊。 這個選項是僅適用於成員變數加入至類別，衍生自[CDialog](../mfc/reference/cdialog-class.md)。 選取此方塊以啟用**控制項 ID**和**控制項類型**選項。  
  
 **控制項 ID**  
 設定您要加入此控制項變數的識別碼。 從清單中選取的控制項，您要加入成員變數類型的識別碼。 清單是作用中時，才**控制變數**選取方塊，且它僅限於已經加入至對話方塊控制項 Id。 例如，對於標準**確定** 按鈕，控制項 ID 是**IDOK**。  
  
|選項|描述|  
|------------|-----------------|  
|**控制項**|控制項類型的預設會設定這個選項。 （如您可能想要與清單方塊、 下拉式方塊中或編輯方塊），它會管理本身，而非從狀態或內容控制項的控制項。|  
|**值**|此選項可只可包含的值 （例如編輯方塊），或反映工作狀態 （例如核取方塊），控制項類型及可能用來管理範圍、 內容或狀態。 請參閱[對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)如需詳細資訊。|  
  
 **分類**  
 指定變數根據控制項類型或控制項的值。  
  
 **控制項類型**  
 設定要加入的控制項類型。 無法變更使用此方塊。 例如，在按鈕的控制項類型**按鈕**，下拉式方塊擁有的控制項類型和**COMBOBOX**。 請參閱[對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)如需詳細資訊。  
  
 **最大字元數**  
 時才可使用**變數型別**設[CString](../atl-mfc-shared/reference/cstringt-class.md)。 表示控制項可以容納字元的數目上限。  
  
 **最小值**  
 變數的類型時，才能使用**BOOL**， `int`， **UINT**，**長**， `DWORD`， **float**， **double**，**位元組**，**簡短**， [COLECurrency](../mfc/reference/colecurrency-class.md)或[CTime](../atl-mfc-shared/reference/ctime-class.md)。 表示可接受的小數位數或日期範圍的最小值。  
  
 **最大值**  
 變數的類型時，才能使用**BOOL**， `int`， **UINT**，**長**， `DWORD`， **float**， **double**，**位元組**，**簡短**，`COLECurrency`或`CTime`。 表示可接受的小數位數或日期範圍的最大值。  
  
 **.h 檔案**  
 ActiveX 控制項，其成員變數需要包裝函式的類別。 設定要加入類別宣告的標頭檔的名稱。  
  
 **.cpp 檔案中**  
 ActiveX 控制項，其成員變數需要包裝函式的類別。 設定要加入類別定義的實作檔案的名稱。  
  
 **註解**  
 提供成員變數的標頭檔中的註解。  
  
## <a name="see-also"></a>請參閱  
 [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)