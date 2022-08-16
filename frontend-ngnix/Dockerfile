#get baseImage
FROM node:16-alpine as builder

#dependencies are installed in this path w.r.t context build provided while building image
#if . is context -> path will be ./usr/app
#if ./mydir/app is context path will be ./mydir/app/user/app
WORKDIR /workarea/app

#copy the dependency file into base image which will be used by next instruction
# copy  -> ./package.json ./usr/app
# below way helps run npm instruction to run only if there is any change in the package.json
#any change in other files does not affect the npm install step
COPY ./package.json ./
RUN npm install

#copy the dependency file into base image working directory path
COPY ./ ./

#whenever container is started use the below command to start npm
RUN npm run build

#now the build we there in the -> /workarea/app/build

FROM nginx
COPY --from=builder /workarea/app/build /usr/share/nginx/html
