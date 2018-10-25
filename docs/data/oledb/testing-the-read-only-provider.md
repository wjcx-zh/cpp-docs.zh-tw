---
title: 測試唯讀提供者 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 309dc98988e4ae4fb1edd75bfb303fc8d9b078cd
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059138"
---
# <a name="testing-the-read-only-provider"></a>測試唯讀提供者

若要測試的提供者，您需要取用者。 如果取用者可以對應與提供者會最好。 OLE DB 消費者樣板是 OLE DB 的精簡型包裝函式，且符合提供者 COM 物件。 因為來源隨附消費者樣板，很容易偵錯與他們的提供者。 消費者樣板還有開發取用者應用程式很小且更快速的方法。

本主題中的範例會建立預設的 MFC 應用程式精靈應用程式的測試用戶。 測試應用程式是簡單的對話方塊與加入的 OLE DB 消費者範本程式碼。

## <a name="to-create-the-test-application"></a>若要建立測試應用程式

1. 按一下 [ **檔案** ] 功能表上的 [ **新增**]，然後按一下 [ **專案**]。

1. 在 **專案類型**窗格中，選取**Visual c + + 專案**資料夾。 在 **範本**窗格中，選取**MFC 應用程式**。

1. 針對專案名稱，輸入*TestProv*，然後按一下**確定**。

   MFC 應用程式精靈 隨即出現。

1. 在 **應用程式類型**頁面上，選取**採用對話方塊**。

1. 在 **進階功能**頁面上，選取**自動化**，然後按一下**完成**。

> [!NOTE]
> 如果您新增應用程式不需要自動化支援`CoInitialize`在`CTestProvApp::InitInstance`。

您可以檢視及編輯**TestProv**中選取它的對話方塊 (IDD_TESTPROV_DIALOG)**資源檢視**。 將兩個清單方塊，一個用於資料列集，每個字串放在對話方塊中。 關閉排序屬性的同時清單方塊按下**Alt**+**Enter**選取清單方塊時，按一下**樣式**索引標籤，然後清除**排序**核取方塊。 此外，放置**執行**來擷取檔案的對話方塊上的按鈕。 已完成**TestProv**  對話方塊中應該有兩個分別標示為 「 字串 1 」 和 「 String 2"的清單方塊，它也有**確定**，**取消**，和**執行**按鈕。

開啟對話方塊類別 （在此案例的 TestProvDlg.h) 的標頭檔。 下列程式碼加入標頭檔 （之外的任何類別宣告）：

```cpp
////////////////////////////////////////////////////////////////////////
// TestProvDlg.h

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

程式碼代表定義資料行都會出現的資料列集的使用者記錄。 當用戶端呼叫`IAccessor::CreateAccessor`，它會使用這些項目指定要繫結的資料行。 OLE DB 消費者範本也可讓您動態繫結資料行。 COLUMN_ENTRY 巨集是用戶端版本 PROVIDER_COLUMN_ENTRY 巨集。 兩個 COLUMN_ENTRY 巨集指定的序數、 兩個字串的型別、 長度和資料成員。

新增處理常式函式，如**執行**藉由按下按鈕**Ctrl** ，並按兩下**執行** 按鈕。 下列程式碼置於函式：

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

void CtestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession   session;

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

`CCommand`， `CDataSource`，和`CSession`全部都屬於 OLE DB 消費者範本的類別。 每個類別會模擬 COM 物件提供者中。 `CCommand`物件會`CProvider`標頭檔，做為範本參數中宣告的類別。 `CProvider`參數代表您用來從提供者存取的資料繫結。 以下是`Open`資料來源、 工作階段和命令的程式碼：

```cpp
if (source.Open("Custom.Custom.1", NULL) != S_OK)
   return;

if (session.Open(source) != S_OK)
   return;

if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)
   return;
```

線條以開啟每個類別建立提供者中的每個 COM 物件。 若要尋找的提供者，使用`ProgID`的提供者。 您可以取得`ProgID`從系統登錄，或是查看 Custom.rgs 檔案中 (開啟提供者的目錄，並搜尋`ProgID`索引鍵)。

MyData.txt 檔會包含與`MyProv`範例。 若要建立您自己的檔案，請使用編輯器，並輸入偶數數目的按下 ENTER，每個字串之間的字串。 如果您移動檔案，請變更路徑名稱。

傳遞字串"c:\\\samples\\\myprov\\\MyData.txt 」 中`table.Open`列。 如果您逐步執行`Open`呼叫中，您會看到這個字串會傳遞至`SetCommandText`提供者中的方法。 請注意，`ICommandText::Execute`使用該字串的方法。

若要擷取的資料，請呼叫`MoveNext`資料表上。 `MoveNext` 呼叫`IRowset::GetNextRows`， `GetRowCount`，和`GetData`函式。 有沒有更多的資料列時 (也就是資料列集的目前位置大於`GetRowCount`)，迴圈便會終止：

```cpp
while (table.MoveNext() == S_OK)
{
   m_ctlString1.AddString(table.szField1);
   m_ctlString2.AddString(table.szField2);
}
```

請注意，沒有其他資料列時，提供者會傳回 DB_S_ENDOFROWSET。 DB_S_ENDOFROWSET 值不是錯誤。 您應該一律檢查針對 S_OK 取消資料擷取迴圈，而不使用 SUCCEEDED 巨集。

您現在應該能夠建置和測試程式。

## <a name="see-also"></a>另請參閱

[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)