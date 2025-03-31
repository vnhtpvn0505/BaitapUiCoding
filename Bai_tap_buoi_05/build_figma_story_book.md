# Design System - Figma to StoryBook
##  Bước 1.    Cài đặt plugin kết nối storybook Figma
### https://www.chromatic.com/docs/figma-plugin/ -Storybook  Connect
### story.to.design

##  Bước 2.   Publish link StoryBook
### 1.  Login to  https://www.chromatic.com/apps 
### 2.  Tạo Projeccts mới trên Github
### 3.   Add Project => Choose from Github Project => Chọn Project đã tạo trên Github => Chọn Storybook Project
### 4.   Run cmd npm install --save-dev chromatic
### 4.   Add code vào  file package.json
```json
{
  "name": "demo-storybook",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "storybook": "storybook dev -p 6006",
    "build-storybook": "storybook build",
    "chromatic": "chromatic --project-token=c3146ffd-b275-46b2-ab61-2a24bcb2ec49"
  },
  "devDependencies": {
    "@chromatic-com/storybook": "3",
    "@storybook/addon-designs": "^8.2.1",
    "@storybook/addon-essentials": "8.6.11",
    "@storybook/addon-onboarding": "8.6.11",
    "@storybook/blocks": "8.6.11",
    "@storybook/experimental-addon-test": "8.6.11",
    "@storybook/nextjs": "8.6.11",
    "@storybook/react": "8.6.11",
    "@storybook/test": "8.6.11",
    "storybook": "8.6.11"
  },
  "dependencies": {
    "next": "^15.2.4",
    "prop-types": "^15.8.1",
    "react": "^19.1.0",
    "react-dom": "^19.1.0"
  }
}
``` 
### 5.   Chạy lệnh    npx storybook init
### 5.   Chạy lệnh    npx chromatic --project-token=c3146ffd-b275-46b2-ab61-2a24bcb2ec49

