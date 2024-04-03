---
layout: page
title: О проекте
permalink: /temp/
---

Ты можешь проходить финальное задание курса или просто использовать это окружение как Ansible playgroung.
Доступы к серверам находятся в разделе Wiki


<script src="/jquery.min.js"></script>


<div>
    <div class="attachment-data"></div>
    
      <div id="rt_scenario" name="ansible-universal" lab="00010-find"></div>
    
</div>


<script>
    var scenario_div_name = '#rt_scenario';
    
    var startLab = function(){
        $('#start-lab-button').remove();
        
        var scenario_name = $(scenario_div_name).attr('name')
        var lab_name = $('#rt_scenario').attr("lab")
        var data_katacoda_command = "";
        if(lab_name){
            data_katacoda_command="export SCENARIO_NAME=" + lab_name + ";";
        }
        
        var div_source_code = '<div id="katacoda-scenario-1" data-katacoda-command="' + data_katacoda_command + '" data-katacoda-hideintro="false" data-katacoda-id="rotoro-practice/' + scenario_name + '" data-katacoda-externalcss="https://raw.githubusercontent.com/rotoro-cloud/rotoro-cloud.github.io/master/labEnv.css" data-katacoda-color="004d7f" style="height: 90vh;">';
        $(scenario_div_name).append(div_source_code);    
        var embed_script = document.createElement('script');
        embed_script.setAttribute('src','https://katacoda.com/embed.js?cache=rt');
        
        if($(scenario_div_name + ' script').length == 0){
            $(scenario_div_name).append(embed_script);
        }
    
        
        
        $.post( window.location.pathname + "/complete", function() {
          console.log("lecture completed")
        })
          .done(function() {
            console.log("lecture done")
          })
          .fail(function() {
            console.log("lecture complete failed")
          })
          .always(function() {
            console.log("lecture complete finished")
          });
        
        
    }
    
    var div_button_source_code = '<div id="start-lab-button" style="text-align: center; margin-top: 10px;"><a class="btn btn-md btn-primary" onclick="startLab()" ><img src="https://raw.githubusercontent.com/rotoro-cloud/rotoro-cloud.github.io/master/images/ansible1/lab8.jpg">Запуск упражнения</a><br><br><a href="https://rotoro.cloud/troubleshooting-labs" target="_blank">Если возникли проблемы, смотри здесь</a></div>';
    
    $(scenario_div_name).append(div_button_source_code);  

</script>


<script>
  
  $(document).ready(function() { 
    if($('#rt_feedback_form')){
    var course=$('#rt_feedback_form').attr('course')
    var section=$('#rt_feedback_form').attr('section')
    
    var entries = ""
    if(typeof userid !== 'undefined'){
        var entries="&entry.1103390199=" + section + "-" + userid
    }
    
  }
    
  });
  
</script>
