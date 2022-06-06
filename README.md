# LIMO_ROS2_VSC_Container
 
Playrobot Inc. AkinoKotori製作

LIMO的ROS2環境需要使用Container，但建立指令偏多且需要變更部分原始碼

此包為VSCode可使用之Container配置，下載：

```bash
git clone https://github.com/PlayRobotWiki/LIMO_ROS2_VSC_Container
```

安裝VSCode的兩個插件：Docker和Remote-Container

接著打開VSCode >> File >> Open Folder >> Show Local >> Desktop >> LIMO_ROS2_VSC_Container >> OK

配置後僅需編譯LIMO ROS2 Package即可使用，點選Terminal >> New後輸入以下三行指令：

```bash
cd ..
colcon build --symlink-install
echo "source /workspaces/install/setup.bash" >> ~/.bashrc
```
