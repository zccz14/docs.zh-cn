---
title: "WCF 的 &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c196f6d7-77f6-4266-973c-305b2b4dd8a2
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# WCF 的 &lt;add&gt;
配置一个跟踪参与者，它侦听直接从运行时发出的跟踪记录，并按照配置跟踪参与者的任何方式处理这些记录。  这包括写入特定输出（例如，文件、控制台、ETW）、处理\/聚合记录或可能需要的任何其他组合。  
  
 有关工作流跟踪和跟踪参与者的更多信息，请参见[工作流跟踪](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)和[跟踪参与者](../../../../../docs/framework/windows-workflow-foundation//tracking-participants.md)。  
  
## 语法  
  
```vb  
  
<tracking>   
   <participants>   
      <add name="String"   
           profileName="String"  
           type="String" />   
   </participants>   
</tracking>  
  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|元素|描述|  
|--------|--------|  
|name|一个字符串，指定跟踪参与者的名称。|  
|profileName|一个字符串，指定跟踪配置文件的名称，该跟踪配置文件定义跟踪参与者已订阅的跟踪记录。|  
|类型|一个字符串，指定跟踪参与者的类型。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[\<participants\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|跟踪参与者的列表|  
  
## 备注  
 跟踪参与者用于获取从工作流发出的跟踪数据并将其存储在不同的媒体中。  同样，也可以在跟踪参与者中执行对跟踪记录的任何后续处理。  
  
 多个跟踪参与者可同时使用跟踪事件。  每个跟踪参与者都可与不同的跟踪配置文件关联。  
  
 提供了将跟踪记录写入 ETW 会话的标准跟踪参与者。  通过在配置文件中添加特定于跟踪的行为，可以对工作流服务配置参与者。  通过启用 ETW 跟踪参与者，可以在事件查看器中查看跟踪记录。  如果这不能满足您的要求，您还可以编写自定义跟踪参与者。  
  
## 示例  
 下面的配置示例演示在 Web.config 文件中配置的标准 ETW 跟踪参与者。  
  
 ETW 跟踪参与者用于将跟踪记录写入 ETW 的提供程序 ID 在 `<diagnostics>` 节中定义。  跟踪参与者具有一个与其关联的配置文件，用来指定跟踪参与者已订阅的跟踪记录。  它由 `<add>` 元素的 `profileName` 特性进行定义。  定义这些内容后，跟踪参与者将被添加到 `<etwTracking>` 服务行为中。  这会将所选跟踪参与者添加到工作流实例的扩展中，以便它们开始接收跟踪记录。  
  
```  
  
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## 请参阅  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>   
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>   
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehavior>   
 [工作流跟踪](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [跟踪参与者](../../../../../docs/framework/windows-workflow-foundation//tracking-participants.md)