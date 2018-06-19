---
title: 裝載 Windows 形成使用者控制項，MFC 對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b356bff4974b43445524d9bc07e1e37c62a6f8d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138674"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>將 Windows Form 使用者控制項裝載成 MFC 對話方塊
MFC 提供此範本類別[CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) ，讓您可以裝載 Windows Form 使用者控制項 (<xref:System.Windows.Forms.UserControl>) 強制或非強制回應 MFC 對話方塊中。 `CWinFormsDialog` 從 MFC 類別衍生[CDialog](../mfc/reference/cdialog-class.md)，因此可以啟動為強制回應或非強制回應對話方塊。  
  
 處理程序，`CWinFormsDialog`用來將使用者控制項裝載很相似述[MFC 對話方塊中的 Windows Form 使用者控制項裝載](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)。 不過，`CWinFormsDialog`管理的初始化和裝載使用者控制項，讓它不需要以手動方式進行程式設計。  
  
 顯示與 MFC 一起使用的 Windows Form 的範例應用程式，請參閱[MFC 和 Windows Form 整合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
### <a name="to-create-the-mfc-host-application"></a>若要建立 MFC 主應用程式  
  
1.  建立 MFC 應用程式專案。  
  
     在**檔案**功能表上，選取**新增**，然後按一下 **專案**。 在**Visual c + +** 資料夾中，選取**MFC 應用程式**。  
  
     在**名稱**方塊中，輸入`MFC03`並將方案設定變更為**將加入至方案**。按一下**確定**。  
  
     在**MFC 應用程式精靈**，接受所有預設值，然後按**完成**。 這會建立多重文件介面 MFC 應用程式。  
  
2.  設定專案。  
  
     在**方案總管] 中**，以滑鼠右鍵按一下**MFC03**專案節點，然後選擇 [**屬性**。 **屬性頁** 對話方塊隨即出現。  
  
     在**屬性頁**對話方塊中，於**組態屬性**樹狀結構控制項中選取**一般**，接著在**專案預設值**區段中，將**Common Language Runtime 支援**至**Common Language Runtime 支援 (/ clr)**。 按一下 [確定 **Deploying Office Solutions**]。  
  
3.  新增.NET 控制項的參考。  
  
     在**方案總管] 中**，以滑鼠右鍵按一下**MFC03**專案節點，然後選擇 [**新增**，**參考**。 在**屬性頁**，按一下**加入新參考**，選取 WindowsControlLibrary1 (下**專案** 索引標籤)，然後按一下**確定**。 這將參考加入的形式[/FU](../build/reference/fu-name-forced-hash-using-file.md)編譯器選項，使程式會進行編譯，也會複製到 WindowsControlLibrary1.dll`MFC03`專案目錄，以便執行程式。  
  
4.  新增`#include <afxwinforms.h>`為 stdafx.h，結尾的現有`#include`陳述式。  
  
5.  加入新類別的子類別`CDialog`。  
  
     以滑鼠右鍵按一下專案名稱，並加入 MFC 類別 (稱為 CHostForWinForm) 的子類別`CDialog`。 由於您不需要對話方塊資源，您可以刪除的資源識別碼 （選取 資源檢視、 展開對話方塊 資料夾，並刪除 IDD_HOSTFORWINFORM 資源。  然後，移除任何參考的識別碼在程式碼中。）。  
  
6.  取代`CDialog`CHostForWinForm.h 和 CHostForWinForm.cpp 檔案中與`CWinFormsDialog<WindowsControlLibrary1::UserControl1>`。  
  
7.  呼叫 DoModal CHostForWinForm 類別上。  
  
     在 MFC03.cpp，加入`#include "HostForWinForm.h"`。  
  
     傳回陳述式之前的 CMFC03App::InitInstance 定義中，加入：  
  
     `CHostForWinForm m_HostForWinForm;`  
  
     `m_HostForWinForm.DoModal();`  
  
8.  建置並執行專案。  
  
     在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
     在**偵錯**功能表上，按一下 **啟動但不偵錯**。  
  
     接下來您將加入程式碼以監視從 MFC 應用程式在 Windows Form 上控制項的狀態。  
  
9. OnInitDialog 加入處理常式。  
  
     顯示**屬性**視窗 (F4)。 在**類別檢視**，選取 CHostForWinForm。 在**屬性**視窗中，選取覆寫並在 OnInitDialog 列中，按一下左側資料行中，然後選取\<新增 >。 這會將下行加入 CHostForWinForm.h:  
  
    ```  
    virtual BOOL OnInitDialog();  
    ```  
  
10. 定義 OnInitDialog （在 CHostForWinForm.cpp)，如下所示：  
  
    ```  
    BOOL CHostForWinForm::OnInitDialog() {  
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();  
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);  
       return TRUE;  
    }  
    ```  
  
11. 接下來請加入 OnButton1 處理常式。 將下列幾行加入至公開的一節中 CHostForWinForm.h CHostForWinForm 類別：  
  
    ```  
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );  
  
    BEGIN_DELEGATE_MAP( CHostForWinForm )  
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );  
    END_DELEGATE_MAP()  
    ```  
  
     在 CHostForWinForm.cpp，加入此定義：  
  
    ```  
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )   
    {  
       System::Windows::Forms::MessageBox::Show("test");  
    }  
    ```  
  
12. 建置並執行專案。 當您按一下按鈕，這是在 Windows Form 上，在 MFC 應用程式的程式碼會執行。  
  
     接下來您將加入程式碼，以顯示從 MFC 程式碼中的值 Windows Form 上的文字方塊。  
  
13. 在中 CHostForWinForm.h CHostForWinForm 類別的公用區段中，加入下列宣告：  
  
    ```  
    CString m_sEditBoxOnWinForm;  
    ```  
  
14. 在中 CHostForWinForm.cpp DoDataExchange 定義中，加入下列三行函式的結尾：  
  
    ```  
    if (pDX->m_bSaveAndValidate)  
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);  
    else  
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);  
    ```  
  
15. 在中 CHostForWinForm.cpp OnButton1 定義中，加入下列三行函式的結尾：  
  
    ```  
    this->UpdateData(TRUE);  
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);  
    System::Windows::Forms::MessageBox::Show(z);  
    ```  
  
16. 建置並執行專案。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>   
 [在 MFC 中使用 Windows Forms 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)