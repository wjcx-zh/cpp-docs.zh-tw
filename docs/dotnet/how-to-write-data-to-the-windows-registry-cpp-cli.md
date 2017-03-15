---
title: "如何：將資料寫入至 Windows 登錄 (C++/CLI) | Microsoft Docs"
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
  - "登錄, 寫入至"
  - "Visual C++, 寫入至 Windows 登錄"
ms.assetid: 3d40b978-4baa-4779-bfe3-47e2917b757f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：將資料寫入至 Windows 登錄 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會使用 <xref:Microsoft.Win32.Registry.CurrentUser> 金鑰，以建立對應至 **Software** 金鑰之 <xref:Microsoft.Win32.RegistryKey> 類別的可寫入執行個體。  然後，再使用 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> 方法建立新的金鑰，並將它加入金鑰\/值組中。  
  
## 範例  
  
### 程式碼  
  
```  
// registry_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main()  
{  
   // The second OpenSubKey argument indicates that  
   // the subkey should be writable.   
   RegistryKey^ rk;  
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);  
   if (!rk)  
   {  
      Console::WriteLine("Failed to open CurrentUser/Software key");  
      return -1;  
   }  
  
   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");  
   if (!nk)  
   {  
      Console::WriteLine("Failed to create 'NewRegKey'");  
      return -1;  
   }  
  
   String^ newValue = "NewValue";  
   try  
   {  
      nk->SetValue("NewKey", newValue);  
      nk->SetValue("NewKey2", 44);  
   }  
   catch (Exception^)  
   {  
      Console::WriteLine("Failed to set new values in 'NewRegKey'");  
      return -1;  
   }  
  
   Console::WriteLine("New key created.");  
   Console::Write("Use REGEDIT.EXE to verify ");  
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");  
   return 0;  
}  
```  
  
## 備註  
 您可以使用 .NET Framework 存取具有 <xref:Microsoft.Win32.Registry> 和 [RegistryKey](https://msdn.microsoft.com/en-us/library/microsoft.win32.registrykey.aspx) 類別的登錄，這兩個類別都是在 <xref:Microsoft.Win32> 命名空間中定義。  **Registry** 類別是 <xref:Microsoft.Win32.RegistryKey> 類別之靜態執行個體的容器。  每個執行個體表示一個根目錄登錄節點。  這些執行個體為 <xref:Microsoft.Win32.Registry.ClassesRoot>、<xref:Microsoft.Win32.Registry.CurrentConfig>、<xref:Microsoft.Win32.Registry.CurrentUser>、<xref:Microsoft.Win32.Registry.LocalMachine> 和 <xref:Microsoft.Win32.Registry.Users>。  
  
## 請參閱  
 [如何：從 Windows 登錄讀取資料](../dotnet/how-to-read-data-from-the-windows-registry-cpp-cli.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)