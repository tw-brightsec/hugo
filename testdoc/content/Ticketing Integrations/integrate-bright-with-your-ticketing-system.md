---
title: "Integrating Bright with Your Ticketing System"
slug: "integrate-bright-with-your-ticketing-system"
hidden: false
metadata: 
  description: "You can view and manage the NeuraLegion reports on every detected vulnerability in the ticketing and communication systems that you use in your development environment. The integration allows you to simplify and accelerate fixing the security issues of your application or API by using automatically created tickets and distributing them among your development team."
createdAt: "2021-09-16T07:31:52.538Z"
updatedAt: "2022-10-11T17:41:21.704Z"
---
You can view and manage the Bright reports on every detected vulnerability in the ticketing and communication systems that you use in your development environment. The integration allows you to simplify and accelerate fixing the security issues of your application or API by using automatically created tickets and distributing them among your development team.  


[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2F7vriwHUvSWw%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D7vriwHUvSWw&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2F7vriwHUvSWw%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=7vriwHUvSWw",
  "title": "How to Integrate Nexploit with Ticketing Systems",
  "favicon": "https://www.youtube.com/s/desktop/3d8e40b0/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/7vriwHUvSWw/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=7vriwHUvSWw"
}
[/block]




## Integration flow

To enable Bright to send the scan reports to multiple repositories (projects, channels) of your ticketing and communication systems, you need to do the following:

1. Connect Bright to the relative systems and select the repositories to which Bright should have access: 

[block:html]
{
  "html": "<table id=\"integrations\" >\n   <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"50%\">\n      <a href=\"/docs/jira\"><img src=\"https://files.readme.io/a466ee8-jira_software_logo-e1571063680300.png\" width=\"220\" height=\"60\"></a>\n    </td>\n    <td width=\"50%\">\n     <a href=\"/docs/github\"><img src=\"https://files.readme.io/af12d01-1_JLYlSLSK8-AZo8gt9UdYqA.jpeg\" width=\"200\" height=\"110\"></a>\n    </td>\n  </tr>\n     <tr>\n    <td width=\"50%\">\n      <a href=\"/docs/slack\"><img src=\"https://files.readme.io/46b4561-2560px-Slack_Technologies_Logo.svg.png\" width=\"200\" height=\"50\"></a>\n    </td>\n    <td width=\"50%\">\n      <a href=\"/docs/gitlab-boards\"><img src=\"https://files.readme.io/aebce8d-download_1.png\" width=\"220\" height=\"75\"></a>\n    </td>\n    </tr>\n    <tr>\n    <td width=\"50%\">\n    <a href=\"/docs/azure-boards\"><img src=\"https://files.readme.io/51d35a2-unnamed.png\" width=\"200\" height=\"55\"></a>\n    </td>\n    </tr>\n</table>\n</body>"
}
[/block]



2. Associate the connected repository(ies) with a specific Bright project, and then select the associated repositories for a new scan. For the instruction, see [Add Ticketing Integration to a Project](doc:add-ticketing-integration-to-a-project).

**Other integrations**

- To read how to configure SSO integration, see [Integrate Bright with Your CI Pipeline](/docs/configure-sso) 
- To read how to configure integration with a CI pipeline, see [Integrate Bright with Your CI Pipeline](doc:integrate-nexploit-with-your-ci-pipeline)