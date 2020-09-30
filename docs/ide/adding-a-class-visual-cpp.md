---
title: 新增類別
ms.date: 05/14/2019
f1_keywords:
- vc.addclass
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
- Add Class dialog box
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
ms.openlocfilehash: b1c64505a63b8720ed7aee855f2bbbbdb9134e28
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505985"
---
# <a name="add-a-class"></a>新增類別

若要在 Visual Studio C++ 專案中新增類別，請以滑鼠右鍵按一下 [方案總管]**** 中的專案，然後依序選擇 [新增]**** 和 [類別]****。 這會開啟 [[新增類別] 對話方塊](#add-class-dialog-box)。

當您新增類別時，您必須指定與 MFC 或 ATL 中已存在類別不同的名稱。 如果您指定的名稱已存在於任一程式庫中，IDE 會顯示錯誤訊息。

如果您的專案命名慣例要求您使用現有的名稱，因為 C++ 會區分大小寫，所以您可以只變更名稱中一或多個字母的大小寫。 例如，雖然您不可以將類別命名為 `CDocument`，但您可以將它命名為 `cdocument`。

## <a name="in-this-section"></a>本節內容

- [您想要新增哪種類別？](#what-kind-of-class-do-you-want-to-add)
- [[新增類別] 對話方塊](#add-class-dialog-box)

## <a name="what-kind-of-class-do-you-want-to-add"></a>您想要新增哪種類別？

在 [新增類別]**** 對話方塊中，當您展開左窗格中的 [Visual C++]**** 節點時，即會顯示已安裝範本的數個群組。 這些群組包含 **CLR**、**ATL**、**MFC** 和 **C++**。 當您選取群組時，中間窗格會顯示該群組中的可用範本清單。 每個範本包含類別所需的檔案和原始程式碼。

若要產生新的類別，請在中間窗格中選取範本，在 [名稱]**** 方塊中鍵入類別名稱，然後選取 [新增]****。 這會開啟 [新增類別精靈]****，以供您指定類別的選項。

- 如需如何建立 MFC 類別的詳細資訊，請參閱 [MFC 類別](../mfc/reference/adding-an-mfc-class.md)。

- 如需如何建立 ATL 類別的詳細資訊，請參閱 [ATL 簡易物件](../atl/reference/adding-an-atl-simple-object.md)。

> [!NOTE]
> [將 ATL 支援新增至 MFC]**** 範本不會建立類別，而是設定專案使用 ATL。 如需詳細資訊，請參閱 [MFC 專案中的 ATL 支援](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。

若要建立不使用 MFC、ATL 或 CLR 的 C++ 類別，請使用已安裝範本之 **C++** 群組中的 [C++ 類別]**** 範本。 如需詳細資訊，請參閱[新增泛型 C++ 類別](../ide/adding-a-generic-cpp-class.md)。

表單架構的 C++ 類別有兩種。 第一種是 [CFormView 類別](../mfc/reference/cformview-class.md)，可建立 MFC 類別。 第二種可建立 CLR Windows Forms 類別。

## <a name="add-class-dialog-box"></a>加入類別對話方塊

[加入類別] **** 對話方塊包含的範本可讓您：

- 開啟對應的程式碼精靈，如果有的話。 如需詳細資訊，請參閱[使用程式碼精靈新增功能](../ide/adding-functionality-with-code-wizards-cpp.md)。

   \- 或 -

- 在專案中加入適當的檔案和原始程式碼，自動建立新類別。

您可以從 [專案]**** 功能表、[方案總管]**** 或[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)，存取 [新增類別]**** 對話方塊。

> [!NOTE]
> 當您嘗試加入不適合目前專案的類別時，您會收到錯誤訊息。 選取 [確定]**** 返回 [新增類別]**** 對話方塊。

### <a name="add-class-templates"></a>[新增類別] 範本

[加入類別] **** 範本有四個類別：.NET、ATL、MFC 和泛型。 當您在 [範本] **** 窗格中選取範本時，描述選項的文字會出現在 [類別] **** 和 [範本] **** 窗格下。

#### <a name="net"></a>.NET

|[範本]|精靈|
|--------------|------------|
|ASP.NET Web 服務|尚未提供|
|元件類別 (.NET)|尚未提供|
|安裝程式類別 (.NET)|尚未提供|
|使用者控制項 (.NET)|尚未提供|
|Windows Form (.NET)|尚未提供|

#### <a name="atl"></a>ATL

|[範本]|精靈|
|--------------|------------|
|將 ATL 支援加入 MFC|尚未提供|
|ATL 控制項|[ATL 控制項 wizard](../atl/reference/atl-control-wizard.md)|
|ATL 對話方塊|[ATL 對話方塊 wizard](../atl/reference/atl-dialog-wizard.md)|
|ATL 簡單物件|[ATL 簡單物件 wizard](../atl/reference/atl-simple-object-wizard.md)|
|WMI 事件提供者|WMI 事件提供者精靈|
|WMI 執行個體提供者|WMI 執行個體提供者精靈|

#### <a name="mfc"></a>MFC

|[範本]|精靈|
|--------------|------------|
|MFC 類別|[MFC 加入類別 wizard](../mfc/reference/mfc-add-class-wizard.md)|

#### <a name="generic-classes"></a>泛型類別

|[範本]|精靈|
|--------------|------------|
|泛型 C++ 類別|[泛型 c + + 類別 wizard](./adding-a-generic-cpp-class.md#generic-c-class-wizard)|
