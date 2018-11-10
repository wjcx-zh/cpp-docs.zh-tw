---
title: 加入成員變數精靈
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.variable.overview
helpviewer_keywords:
- Add Member Variable Wizard [C++]
ms.assetid: 73e8fa99-ac1a-42e2-8fc2-4684b9eb6d4d
ms.openlocfilehash: ea9b52c7448ee46a15c5da541784378d2b625d88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598584"
---
# <a name="add-member-variable-wizard"></a>加入成員變數精靈

此精靈會將成員變數宣告新增至標頭檔，而且視選項而定，還可以將程式碼新增至 .cpp 檔案。 一旦您使用精靈新增成員變數，就可以在開發環境中編輯程式碼。

- **存取權**

   設定成員變數的存取權。 存取修飾詞是指定其他類別對成員變數所具有之存取權的關鍵字。 如需指定存取權的詳細資訊，請參閱[成員存取控制](../cpp/member-access-control-cpp.md)。 成員變數存取層級預設為 **public**。

- [public](../cpp/public-cpp.md)

- [protected](../cpp/protected-cpp.md)

- [private](../cpp/private-cpp.md)

- **變數類型**

   設定您要新增之成員變數的傳回型別。

   - 如果您想要新增非對話方塊控制項的成員變數，請從可用類型清單中選取。

      如需這些型別的資訊，請參閱[基本型別](../cpp/fundamental-types-cpp.md)。

      |||
      |-|-|
      |**char**|**short**|
      |**double**|**unsigned char**|
      |**float**|**unsigned int**|
      |**int**|**unsigned long**|
      |**long**||

   - 如果您想要新增對話方塊控制項的成員變數，此方塊會填入針對控制項或值傳回的物件類型。 如果您選取 [控制項]，則 [變數類型] 會指定您在 [控制項識別碼] 方塊中選取之控制項的基底類別。 如果對話方塊控制項可以包含值，且您選取 [值]，則 [變數類型] 會指定該控制項可包含之值的適當類型。 如需詳細資訊，請參閱[對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)。

      此值取決於 [控制項識別碼] 中的選擇，而且無法變更。

- **變數名稱**

   設定您要新增之成員變數的名稱。 成員變數通常是以預設為您提供的識別字串 "m_" 開頭。

- **控制變數**

   表示成員變數會管理具有[資料交換和資料驗證](../mfc/dialog-data-exchange-and-validation.md)支援之對話方塊中的控制項。 如需詳細資訊，請參閱 [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)。 此選項僅適用於新增至衍生自 [CDialog](../mfc/reference/cdialog-class.md) 之類別的成員變數。 選取此方塊可啟用 [控制項識別碼] 和 [控制項類型] 選項。

- **控制項識別碼**

   設定您要新增之控制變數的識別碼。 從您要新增成員變數之控制項類型的識別碼清單中選取。 此清單只有在選取 [控制變數] 方塊時才能使用，而且它僅限於已新增至對話方塊的控制項識別碼。 例如，標準 [確定] 按鈕的控制項識別碼為 **IDOK**。

   |選項|描述|
   |------------|-----------------|
   |**控制項**|控制項類型預設會設定此選項。 它會管理控制項本身，而不是控制項的狀態或內容 (您可能會想要對清單方塊、下拉式方塊或編輯方塊執行此動作)。|
   |**值**|此選項僅適用於包含值 (例如編輯方塊) 或反映狀態 (例如核取方塊) 的控制項類型；針對這些類型，您可能會管理其範圍、內容或狀態。 如需詳細資訊，請參閱[對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)。|

- **分類**

   指定變數是根據控制項類型或控制項的值。

- **控制項類型**

   設定要新增之控制項的類型。 您無法變更此方塊。 例如，按鈕的控制項類型為 **BUTTON**，而下拉式方塊的控制項類型為 **COMBOBOX**。 如需詳細資訊，請參閱[對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)。

- **最大字元數**

   僅適用於 [變數類型] 設定為 [CString](../atl-mfc-shared/reference/cstringt-class.md) 時。 表示控制項可容納的最大字元數。

- **最小值**

   僅適用於變數類型為 **BOOL**、`int`、**UINT**、**long**、`DWORD`、**float**、**double**、**BYTE**、**short**、[COLECurrency](../mfc/reference/colecurrency-class.md) 或 [CTime](../atl-mfc-shared/reference/ctime-class.md) 時。 表示刻度或日期範圍可接受的最小值。

- **最大值**

   僅適用於變數類型為 **BOOL**、`int`、**UINT**、**long**、`DWORD`、**float**、**double**、**BYTE**、**short**、 `COLECurrency` 或 `CTime` 時。 表示刻度或日期範圍可接受的最大值。

- **.h 檔案**

   適用於其成員變數需要包裝函式類別的 ActiveX 控制項。 設定要新增類別宣告之標頭檔的名稱。

- **.cpp 檔案**

   適用於其成員變數需要包裝函式類別的 ActiveX 控制項。 設定要新增類別定義之實作檔的名稱。

- **註解**

   提供成員變數之標頭檔中的註解。

## <a name="see-also"></a>請參閱

[新增成員變數](../ide/adding-a-member-variable-visual-cpp.md)