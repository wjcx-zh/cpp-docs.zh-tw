---
title: 測試唯讀提供者
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
ms.openlocfilehash: a173e1466179dfb40a33d7bdb4a94eabdbf23cc0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079053"
---
# <a name="testing-the-read-only-provider"></a>測試唯讀提供者

若要測試提供者，您需要取用者。 如果取用者能夠與提供者相符，就會有説明。 OLE DB 取用者範本是 OLE DB 的精簡型包裝函式，並與提供者 COM 物件相符。 因為來源隨附于取用者範本，所以很容易就能使用它們來對提供者進行偵錯工具。 取用者範本也是開發取用者應用程式的極小且快速的方式。

本主題中的範例會為測試取用者建立預設的 MFC 應用程式精靈應用程式。 測試應用程式是一個簡單的對話方塊，其中新增了 OLE DB 取用者範本程式碼。

## <a name="to-create-the-test-application"></a>建立測試應用程式

1. 在 **[檔案]** 功能表上按一下 **[新增]** ，然後按一下 **[專案]** 。

1. 在 [**專案類型**] 窗格中，選取 [**已安裝**的 > **Visual C++**  > **MFC/ATL**資料夾]。 在 [**範本**] 窗格中，選取 [ **MFC 應用程式**]。

1. 在 [專案名稱] 中，輸入*TestProv*，然後按一下 **[確定]** 。

   [ **MFC 應用程式**嚮導] 隨即出現。

1. 在 [**應用程式類型**] 頁面上，選取 [以**對話方塊為基礎]** 。

1. 在 [ **Advanced Features** ] 頁面上，選取 [ **Automation**]，然後按一下 **[完成]** 。

> [!NOTE]
> 如果您在 `CTestProvApp::InitInstance`中新增 `CoInitialize`，應用程式不需要自動化支援。

您可以在 [**資源檢視**] 中選取 [ **TestProv** ] 對話方塊（IDD_TESTPROV_DIALOG），以進行查看和編輯。 將兩個清單方塊放在對話方塊中，每個資料列集中的每個字串各一個。 按**Alt**+在選取清單方塊時**輸入**，並將**sort**屬性設定為**False**，以關閉兩個清單方塊的排序屬性。 此外，在對話方塊上放置 [**執行**] 按鈕以提取檔案。 [完成**TestProv** ] 對話方塊應分別標示為 "string 1" 和 "string 2" 的兩個清單方塊;它也有 **[確定]、[** **取消**] 和 [**執行**] 按鈕。

開啟對話方塊類別的標頭檔案（在此案例中為 TestProvDlg）。 將下列程式碼新增至標頭檔（任何類別宣告之外）：

```cpp
////////////////////////////////////////////////////////////////////////
// TestProvDlg.h
#include <atldbcli.h>  

class CProvider
{
// Attributes
public:
   char   szField1[16];
   char   szField2[16];

   // Binding Maps
BEGIN_COLUMN_MAP(CProvider)
   COLUMN_ENTRY(1, szField1)
   COLUMN_ENTRY(2, szField2)
END_COLUMN_MAP()
};
```

此程式碼代表使用者記錄，其定義資料列集中將會有哪些資料行。 當用戶端呼叫 `IAccessor::CreateAccessor`時，它會使用這些專案來指定要系結的資料行。 OLE DB 取用者範本也可讓您以動態方式系結資料行。 COLUMN_ENTRY 宏是 PROVIDER_COLUMN_ENTRY 宏的用戶端版本。 這兩個 COLUMN_ENTRY 宏會指定兩個字串的序數、類型、長度和資料成員。

按**Ctrl**並按兩下 [**執行**] 按鈕，以加入 [**執行**] 按鈕的處理常式函式。 將下列程式碼放在函式中：

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession session;

   if (source.Open("Custom.Custom.1", NULL) != S_OK)
      return;

   if (session.Open(source) != S_OK)
      return;

   if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)
      return;

   while (table.MoveNext() == S_OK)
   {
      m_ctlString1.AddString(table.szField1);
      m_ctlString2.AddString(table.szField2);
   }
}
```

`CCommand`、`CDataSource`和 `CSession` 類別全都屬於 OLE DB 取用者範本。 每個類別都會模仿提供者中的 COM 物件。 `CCommand` 物件會採用在標頭檔中宣告為範本參數的 `CProvider` 類別。 `CProvider` 參數代表您用來從提供者存取資料的系結。

用來開啟每個類別的行都會在提供者中建立每個 COM 物件。 若要找出提供者，請使用提供者的 `ProgID`。 您可以從系統登錄或查看自訂 .rgs 檔案（開啟提供者的目錄，然後搜尋 `ProgID` 金鑰）取得 `ProgID`。

`MyProv` 範例包含 MyData .txt 檔案。 若要建立您自己的檔案，請使用編輯器並輸入偶數的字串，並在每個字串之間按**enter**鍵。 如果您移動檔案，請變更路徑名稱。

在 `table.Open` 行中傳入字串 "c：\\\samples\\\myprov\\\MyData.txt"。 如果您逐步執行 `Open` 呼叫，您會看到此字串傳遞至提供者中的 `SetCommandText` 方法。 請注意，`ICommandText::Execute` 方法會使用該字串。

若要提取資料，請在資料表上呼叫 `MoveNext`。 `MoveNext` 會呼叫 `IRowset::GetNextRows`、`GetRowCount`和 `GetData` 函數。 當沒有其他資料列（也就是資料列集中的目前位置大於 `GetRowCount`）時，迴圈就會終止。

當沒有其他資料列時，提供者會傳回 DB_S_ENDOFROWSET。 DB_S_ENDOFROWSET 值不是錯誤。 您應該一律檢查 S_OK 以取消資料提取迴圈，而不使用 SUCCEEDED 宏。

您現在應該能夠建立和測試程式。

## <a name="see-also"></a>另請參閱

[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)