# bar-project
이수 시스템 인턴을 진행하며 맡은 프로젝트중 일부이며, Google에서 제공하는 google charts의 timeline chart를 활용하여 차트가 보이도록 하였습니다. 

![timeline](https://user-images.githubusercontent.com/52379503/128651677-070d990e-6dd4-4eca-a975-241bc204a79a.png)

위와 같이 타임라인이 보이도록 하였고 startDay, endDay를 각 item마다 가지고 있으며 그 값을 전달하게 되면 해당 Day값에 맞도록 타임라인 바를 형성해줍니다. 그리고 item이 가지고있는 title이라는 파라메터에 따라 item의 y축 위치가 결정되게 됩니다.

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
