---
title: "使用自訂註冊屬性來登錄延伸模組 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
caps.handback.revision: 3
manager: "douge"
---
# 使用自訂註冊屬性來登錄延伸模組
在某些情況下，您可能需要建立新的登錄屬性，您的擴充功能。  若要加入新的登錄機碼，或將新值加入至現有的金鑰，您可以使用註冊屬性。  新的屬性都必須衍生自<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>，而且必須覆寫<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A>和<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>方法。  
  
## 建立自訂屬性  
 下列程式碼會示範如何建立新的註冊屬性。  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 <xref:System.AttributeUsageAttribute>適用於指定程式要的項目 \(類別、 方法等等\) 相關的屬性，是否就可以使用一次以上，以及是否可繼承的屬性類別。  
  
### 建立登錄機碼  
 下列程式碼，自訂屬性會建立所註冊的 VSPackage 機碼下的自訂子機碼。  
  
```  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
### 建立新的值，在 \[現有的登錄機碼  
 您可以加入現有的索引鍵的自訂值。  下列程式碼會示範如何將新值加入至 VSPackage 登錄機碼。  
  
```  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
  
```