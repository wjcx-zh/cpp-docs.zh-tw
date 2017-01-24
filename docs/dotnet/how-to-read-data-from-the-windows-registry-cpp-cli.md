---
title: "如何：從 Windows 登錄讀取資料 (C++/CLI) | Microsoft Docs"
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
  - "登錄, 讀取"
  - "Visual C++, 從 Windows 登錄讀取"
ms.assetid: aebf52c0-acc7-40e2-adbc-d34e0a1e467e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：從 Windows 登錄讀取資料 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會使用 <xref:Microsoft.Win32.Registry.CurrentUser> 機碼，從 Windows 登錄讀取資料。  首先會使用 <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> 方法列舉子機碼 \(Subkey\)，然後使用 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> 方法開啟 Identities 子機碼。  就像根目錄機碼一樣，每個子機碼都是由 <xref:Microsoft.Win32.RegistryKey> 類別 \(Class\) 所表示。  最後，新的 <xref:Microsoft.Win32.RegistryKey> 物件會用來列舉機碼\/值組。  
  
## 範例  
  
### 程式碼  
  
```  
// registry_read.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main( )  
{  
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );  
  
   Console::WriteLine("Subkeys within CurrentUser root key:");  
   for (int i=0; i<key->Length; i++)  
   {  
      Console::WriteLine("   {0}", key[i]);  
   }  
  
   Console::WriteLine("Opening subkey 'Identities'...");  
   RegistryKey^ rk = nullptr;  
   rk = Registry::CurrentUser->OpenSubKey("Identities");  
   if (rk==nullptr)  
   {  
      Console::WriteLine("Registry key not found - aborting");  
      return -1;  
   }  
  
   Console::WriteLine("Key/value pairs within 'Identities' key:");  
   array<String^>^ name = rk->GetValueNames( );  
   for (int i=0; i<name->Length; i++)  
   {  
      String^ value = rk->GetValue(name[i])->ToString();  
      Console::WriteLine("   {0} = {1}", name[i], value);  
   }  
  
   return 0;  
}  
```  
  
## 備註  
 <xref:Microsoft.Win32.Registry> 類別只是 <xref:Microsoft.Win32.RegistryKey> 的靜態執行個體 \(Instance\) 容器。  每個執行個體表示一個根目錄登錄節點。  這些執行個體為 <xref:Microsoft.Win32.Registry.ClassesRoot>、<xref:Microsoft.Win32.Registry.CurrentConfig>、<xref:Microsoft.Win32.Registry.CurrentUser>、<xref:Microsoft.Win32.Registry.LocalMachine> 和 <xref:Microsoft.Win32.Registry.Users>。  
  
 除了是靜態以外，<xref:Microsoft.Win32.Registry> 類別中的物件是唯讀的。  此外，用來存取登錄物件內容 <xref:Microsoft.Win32.RegistryKey> 類別的執行個體也是唯讀的。  如需如何覆寫這個行為的範例，請參閱 [如何：將資料寫入至 Windows 登錄](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)。  
  
 <xref:Microsoft.Win32.Registry> 類別中還有兩個額外的物件：<xref:Microsoft.Win32.Registry.DynData> 和 <xref:Microsoft.Win32.Registry.PerformanceData>。  這兩個物件都是 <xref:Microsoft.Win32.RegistryKey> 類別的執行個體。  <xref:Microsoft.Win32.Registry.DynData> 物件包含動態登錄資訊，只有 Windows 98 和 Windows Me 支援此資訊。  <xref:Microsoft.Win32.Registry.PerformanceData> 物件可以用來存取使用 Windows 效能監視系統之應用程式的效能計數器資訊。  <xref:Microsoft.Win32.Registry.PerformanceData> 節點表示不是真正儲存在登錄的資訊，因此無法使用 Regedit.exe 來檢視。  
  
## 請參閱  
 [如何：將資料寫入至 Windows 登錄](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)   
 [Windows 作業](../dotnet/windows-operations-cpp-cli.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)