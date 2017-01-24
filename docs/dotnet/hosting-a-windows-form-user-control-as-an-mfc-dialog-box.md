---
title: "將 Windows Form 使用者控制項裝載成 MFC 對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "裝載 Windows Form 控制項 [C++]"
  - "MFC [C++], Windows Form 支援"
  - "Windows Form [C++], 裝載為 MFC 對話方塊"
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將 Windows Form 使用者控制項裝載成 MFC 對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供樣板類別 [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md)，能夠讓您在強制回應或非強制回應的 MFC 對話方塊中裝載 Windows Form 使用者控制項 \(<xref:System.Windows.Forms.UserControl>\)。  `CWinFormsDialog` 是衍生自 MFC 類別 [CDialog](../mfc/reference/cdialog-class.md)，因此可以將對話方塊啟動為強制回應或非強制回應。  
  
 `CWinFormsDialog` 使用來裝載使用者控制項的過程，與[將 Windows Form 使用者控制項裝載至 MFC 對話方塊中](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)中的說明相似。  然而，`CWinFormsDialog` 管理了使用者控制項的初始化和裝載，所以不需要以手動方式進行程式化。  
  
 如需示範 Windows Form 搭配 MFC 使用的範例應用程式，請參閱 [MFC 與 Windows Form 整合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en) \(英文\)。  
  
### 若要建立 MFC 主應用程式  
  
1.  建立 MFC 應用程式專案。  
  
     選取 \[**檔案**\] 功能表上的 \[**新增**\]，然後按一下 \[**專案**\]。  在 \[**Visual C\+\+**\] 資料夾中，選取 \[**MFC 應用程式**\]。  
  
     在 \[**名稱**\] 方塊中，輸入 `MFC03`，並且將方案設定變更為 \[**加入至方案**\]，然後按一下 \[**確定**\]。  
  
     在 \[**MFC 應用程式精靈**\] 中，接受所有預設值，然後按一下 \[**完成**\]。  這樣便會建立具備多重文件介面 \(MDI\) 的 MFC 應用程式。  
  
2.  設定專案。  
  
     在 \[**方案總管**\] 中，以滑鼠右鍵按一下**MFC03**，並選擇 \[**屬性**\]。  \[**屬性頁**\] 對話方塊隨即出現。  
  
     在 \[**屬性頁**\] 對話方塊的 \[**組態屬性**\] 樹狀控制項中，選取 \[**一般**\]，然後在 \[**專案預設值**\] 區段中，將 \[**Common Language Runtime 支援**\] 設定為 \[**Common Language Runtime 支援 \(\/clr\)**\]。  按一下 \[**確定**\]。  
  
3.  將參考加入至 .NET 控制項。  
  
     在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**MFC03**\] 專案節點，並且選擇 \[**加入**\],\[**參考**\]。  在 \[**屬性頁**\] 中，按一下 \[**加入新參考**\]，選取 \[WindowsControlLibrary1\] \(在 \[**專案**\] 索引標籤下\)，然後按一下 \[**確定**\]。  如此會以 [\/FU](../build/reference/fu-name-forced-hash-using-file.md) 編譯器選項的形式加入參考，讓程式可以進行編譯；它也會將 WindowsControlLibrary1.dll 複製到 `MFC03` 專案目錄中，讓程式得以執行。  
  
4.  將 `#include <afxwinforms.h>` 加入到位於現有 `#include` 陳述式尾端的 stdafx.h。  
  
5.  加入一個將 `CDialog` 子類別化的新類別。  
  
     以滑鼠右鍵按一下專案名稱，然後加入一個將 `CDialog` 子類別化的 MFC 類別 \(稱為 CHostForWinForm\)。  因為您不需要此對話方塊資源，所以可以刪除此資源 ID \(選取 \[資源檢視\]，並展開 \[對話方塊\] 資料夾，然後刪除 IDD\_HOSTFORWINFORM 資源。接著，就可以移除程式碼中對此 ID 的任何參考\)。  
  
6.  將 CHostForWinForm.h 和 CHostForWinForm.cpp 檔案中的 `CDialog` 替換為 `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`。  
  
7.  呼叫 CHostForWinForm 類別上的 DoModal。  
  
     在 MFC03.cpp 中，加入 `#include "HostForWinForm.h"`。  
  
     在 CMFC03App::InitInstance 定義中的 return 陳述式之前，加入：  
  
     `CHostForWinForm m_HostForWinForm;`  
  
     `m_HostForWinForm.DoModal();`  
  
8.  建置及執行專案。  
  
     在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
     在 \[**偵錯**\] 功能表上，按一下 \[**啟動但不偵錯**\]。  
  
     接下來，您將會加入程式碼，從 MFC 應用程式監視 Windows Form 上的控制項狀態。  
  
9. 加入 OnInitDialog 的處理常式。  
  
     顯示 \[**屬性**\] 視窗 \(F4\)。  在 \[**類別檢視**\] 中選取 \[CHostForWinForm\]。  在 \[**屬性**\] 視窗中選取 \[覆寫\]，然後在 OnInitDialog 的資料列中按一下左邊的資料行，並選取 \[\<加入\>\]。  如此會將下列程式碼行加入到 CHostForWinForm.h 中：  
  
    ```  
    virtual BOOL OnInitDialog();  
    ```  
  
10. 定義 OnInitDialog \(在 CHostForWinForm.cpp 中\)，如下所示：  
  
    ```  
    BOOL CHostForWinForm::OnInitDialog() {  
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();  
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);  
       return TRUE;  
    }  
    ```  
  
11. 接下來，加入 OnButton1 處理常式。  將下列程式碼行加入到 CHostForWinForm.h 中 CHostForWinForm 類別的 public 區段：  
  
    ```  
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );  
  
    BEGIN_DELEGATE_MAP( CHostForWinForm )  
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );  
    END_DELEGATE_MAP()  
    ```  
  
     在 CHostForWinForm.cpp 中加入下列定義：  
  
    ```  
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )   
    {  
       System::Windows::Forms::MessageBox::Show("test");  
    }  
    ```  
  
12. 建置及執行專案。  當您按一下 Windows Form 上的這個按鈕時，即會執行 MFC 應用程式中的程式碼。  
  
     接下來，您將加入程式碼，以便從 MFC 程式碼顯示 Windows Form 上的文字方塊內的值。  
  
13. 在 CHostForWinForm.h 中 CHostForWinForm 類別的 public 區段內，加入下列宣告：  
  
    ```  
    CString m_sEditBoxOnWinForm;  
    ```  
  
14. 在 CHostForWinForm.cpp 的 DoDataExchange 定義內，將下列三行加入到函式的結尾：  
  
    ```  
    if (pDX->m_bSaveAndValidate)  
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);  
    else  
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);  
    ```  
  
15. 在 CHostForWinForm.cpp 的 OnButton1 定義內，將下列三行加入到函式的結尾：  
  
    ```  
    this->UpdateData(TRUE);  
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);  
    System::Windows::Forms::MessageBox::Show(z);  
    ```  
  
16. 建置及執行專案。  
  
## 請參閱  
 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>   
 [在 MFC 中使用 Windows Form 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)