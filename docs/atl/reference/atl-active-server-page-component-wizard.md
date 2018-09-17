---
title: ATL Active Server Page 元件精靈 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.overview
dev_langs:
- C++
helpviewer_keywords:
- ASP components, creating in ATL
- ATL Active Server Page Component Wizard
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 017dac5f9cba676980629109b53f4b2aec4af940
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713215"
---
# <a name="atl-active-server-page-component-wizard"></a>ATL Active Server Page 元件精靈

此精靈可將 Active Server Pages (ASP) 的元件插入至專案。 Microsoft 網際網路資訊服務 (IIS) 會使用 ASP 元件，其增強的網頁程式開發架構的一部分。

使用此精靈，您可以指定元件的執行緒模型，並彙總支援。 您也可以指定錯誤的資訊介面、 連接點和無限制執行緒封送處理的支援。

## <a name="remarks"></a>備註

從 Visual Studio 2008 開始，此精靈所產生的註冊指令碼會註冊其下的 COM 元件**HKEY_CURRENT_USER**而不是**HKEY_LOCAL_MACHINE**。 若要修改此行為，請設定**為所有使用者的註冊元件**ATL 精靈的選項。

## <a name="names"></a>名稱

指定物件、 介面和類別新增至您的專案的名稱。 除了**簡短名稱**，可以獨立於其他編輯所有其他的方塊。 如果您變更的文字**簡短名稱**，變更會反映在這個頁面中的所有其他方塊的名稱。

如果您變更**Coclass**名稱在 [COM] 區段中，變更會反映在**型別**並**ProgID**方塊中，但**介面**名稱不會變更。 此命名的行為可讓您開發您的控制項時輕鬆地識別所有的名稱。

### <a name="c"></a>C++

提供 c + + 類別建立物件的資訊。

- **簡短名稱**  

   設定物件的根名稱。 名稱可決定`Class`和**Coclass**名稱， **.cpp 檔**並 **.h 檔案**名稱，**介面**名稱，**型別**名稱，而**ProgID**，除非您個別變更這些欄位。

- **.h 檔案**  

   設定新物件類別的標頭檔名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置，或將類別宣告附加至現有的檔案。 如果您選取現有的檔案時，精靈會不將其儲存至選取的位置直到您按一下**完成**精靈中。

   精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成] 時，精靈會提示您指出是否應該將類別宣告附加至檔案的內容。 按一下 [是] 可附加檔案，按一下 [否] 可返回精靈並指定另一個檔案名稱。

- **類別**  

   設定要建立之類別的名稱。 這個名稱根據您在中提供的名稱**簡短名稱**前面 'C'，類別名稱的一般前置詞加上。

- **.cpp 檔**  

   設定新物件類別的實作檔名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置。 在您按一下精靈中的 [完成] 之前，檔案不會儲存至選取的位置。

   精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成] 時，精靈會提示您指出是否應該將類別實作附加至檔案的內容。 按一下 [是] 可附加檔案，按一下 [否] 可返回精靈並指定另一個檔案名稱。

- **使用屬性**  

   指出物件是否使用屬性。 如果您要為屬性化 ATL 專案中新增物件，此選項已選取不可以變更。 也就是說，您可以將屬性化的物件加入建立以屬性支援的專案。

   如果您選取此選項，ATL 專案，並沒有支援的屬性，精靈會提示您指定是否要將屬性支援加入至專案。

   屬性化專案的預設，加入您在設定此選項之後的任何物件會指定為屬性化 （核取方塊已選取）。 您可以清除此方塊，將不會使用屬性的物件。

   請參閱[ATL 專案精靈、 應用程式設定](../../atl/reference/application-settings-atl-project-wizard.md)並[屬性的基本機制](../../windows/basic-mechanics-of-attributes.md)如需詳細資訊。

### <a name="com"></a>COM

提供物件的 COM 功能的相關資訊。

- **Coclass**  

   設定元件類別，其中包含的物件所支援的介面清單的名稱。 如果您的專案或此物件使用屬性，您就無法變更此選項，因為不包含 ATL **coclass**屬性。

- **Type**  

   設定會出現在登錄中 coclass 的物件描述。

- **Interface**  

   設定您建立物件的介面。 這個介面包含將自訂方法。

- **ProgID**  

   設定而不是物件的 CLSID 可用容器的名稱。

## <a name="see-also"></a>另請參閱

[ATL Active Server Page 元件](../../atl/reference/adding-an-atl-active-server-page-component.md)
