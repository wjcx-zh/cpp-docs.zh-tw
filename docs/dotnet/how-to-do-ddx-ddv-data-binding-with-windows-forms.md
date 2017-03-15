---
title: "如何：使用 Windows Form 執行 DDX/DDV 資料繫結 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC [C++], 裝載 Windows Form 控制項"
  - "Windows Form [C++], MFC 支援"
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何：使用 Windows Form 執行 DDX/DDV 資料繫結
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[DDX\_ManagedControl](../Topic/DDX_ManagedControl.md) 會呼叫 [CWinFormsControl::CreateManagedControl](../Topic/CWinFormsControl::CreateManagedControl.md) 以建立與資源控制項 ID 相符的控制項。  如果您是使用 `CWinFormsControl` 控制項 \(位於精靈產生的程式碼\) 的 `DDX_ManagedControl`，就不應該為相同的控制項明確地呼叫 `CreateManagedControl`。  
  
 呼叫在 [CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md) 中的 `DDX_ManagedControl` 以便從資源 ID 中建立控制項。  對於資料交換，您不需要使用 DDX\/DDV 函式和 Windows Form 控制項。  您可以放置程式碼以存取在對話方塊 \(或檢視\) 類別的 `DoDataExchange` 方法中 Managed 控制項的屬性，用此來替代，如下列範例所示。  
  
 下列範例會示範如何繫結原生 C\+\+ 字串至 .NET 使用者控制項。  
  
## 範例  
 下列是 MFC 字串 `m_str` 的 DDX\/DDV 資料繫結以及 .NET 使用者控制項的使用者定義 `NameText` 屬性的範例。  
  
 當 [CDialog::OnInitDialog](../Topic/CDialog::OnInitDialog.md) 第一次呼叫 `CMyDlg::DoDataExchange` 時會建立控制項，所以任何參考 `m_UserControl` 的程式碼都一定會追隨 `DDX_ManagedControl` 呼叫。  
  
 您可以在 [如何：建立使用者控制項並裝載至對話方塊中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)階段建立的 MFC01 應用程式中實作此程式碼。  
  
 將下列程式碼放到 CMFC01Dlg 的宣告中：  
  
```  
class CMFC01Dlg : public CDialog  
{  
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;  
   CString m_str;  
};  
```  
  
## 範例  
 將下列程式碼放到 CMFC01Dlg 的實作中：  
  
```  
void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)  
{  
   CDialog::DoDataExchange(pDX);  
   DDX_ManagedControl(pDX, IDC_CTRL1, m_MyControl);  
  
   if (pDX->m_bSaveAndValidate) {  
      m_str = m_MyControl->textBox1->Text;  
   } else  
   {  
      m_MyControl->textBox1->Text = gcnew System::String(m_str);  
   }  
}  
```  
  
## 範例  
 現在，只需要按一下 \[確定\] 按鈕，即可加入處理常式方法。  按一下 \[**資源檢視**\] 索引標籤，  然後在 \[資源檢視\] 中按兩下 \[`IDD_MFC01_DIALOG`\]，  此對話方塊資源即會出現在 \[資源編輯器\] 中。  然後再按兩下 \[確定\] 按鈕，  
  
 依照下列的方式定義處理常式。  
  
```  
void CMFC01Dlg::OnBnClickedOk()  
{  
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));  
   OnOK();  
}  
```  
  
## 範例  
 將下列程式碼行加入到 BOOL CMFC01Dlg::OnInitDialog\(\) 的實作中。  
  
```  
m_MyControl.GetControl()->textBox1->Text = "hello";  
```  
  
 您現在可以建置並執行應用程式；  請注意，當應用程式關閉時，文字方塊中的任何文字都會顯示在快顯訊息方塊中。  
  
## 請參閱  
 [CWinFormsControl Class](../mfc/reference/cwinformscontrol-class.md)   
 [DDX\_ManagedControl](../Topic/DDX_ManagedControl.md)   
 [CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md)