# Architecture

You can find our software architecture documentation for system requirements in this document.

First, the context diagram of our system and external elements is as follows.

![Context Diagram](./images/context-diagram.jpg)



Also, this is a deployment view that shows the infrastructure for each components.

<table>
<tr><td align="center"><a href="./architecture/IFTA_Deployment_View.md">IFTA Deployment view<br>
<img src="https://github.com/user-attachments/assets/217bcb79-3f64-4034-b285-ac11970d8b80" width="800"></a></td></tr>
</table>




The architecture views below are the main contents of system software architecture.

<table>
<tr>
  <td align="center"><a href="./architecture/Rendering_Aggregation_Module_and_C&C_View.md#module-dependency-diagram">Aircraft Rendering - module uses view<br><img src="https://github.com/user-attachments/assets/6268ac37-59e6-4a07-a9ef-0904f99b66be" width="800"></a>       </td>
      </tr>
  <tr>  
  <td align="center"><a href="./architecture/Rendering_Aggregation_Module_and_C&C_View.md#component--connector-cc-view">Aircraft Rendering - Data repository<br>
        <img src="https://github.com/user-attachments/assets/1c5a44c2-846a-4f79-bf62-751233dc7e82" width="800"></a>
    </td>
</tr>
<tr>
  <td align="center"><a href="./architecture/TConnectionThread_C&C_View.md">Separate UI thread - concurrent components<br>
        <img src="https://github.com/user-attachments/assets/05bd718a-952e-4a37-a8a1-b9064eba0fe4" width="800"></a>
  </td>
</tr>
</table>
