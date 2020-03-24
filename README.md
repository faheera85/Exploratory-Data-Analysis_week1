# Exploratory-Data-Analysis_week1
# As the computer memory was low, i have copied the rang of data to be processed on a txt file.
df <- read.table("C:/Users/f1/Desktop/Coursera/course_3/peer_graded/household_power_consumption_1.txt", header = TRUE, sep = ";")

df <- df[complete.cases(df),]


datetime <- as.POSIXct(paste(df$Date, df$Time), format = "%d/%m/%Y %H:%M:%S")


df <- df[,!(names(df) %in% c("Date","Time"))]
df <- cbind(datetime,df)
df
png("plot1.png", wwidth = 480, height = 480)
plot(df$datetime,df$Global_active_power,type = "l",xlab = " ",ylab = "Global Active Power")
dev.off()

png("plot2.png", width = 480, height = 480)
plot(df$Global_active_power~df$datetime, ylab="Global Active Power(Kilometer)", xlab="")
dev.off()

png("plot3.png", width = 480, height = 480)
with(df, {plot(datetime,Sub_metering_1, xlab = "", ylab = "Energy sub metering")
  + lines(df$datetime,df$Sub_metering_2, col = "blue")
  + lines(df$datetime, df$Sub_metering_3, col="red")})
legend("topright",
       
       legend = c("Sub_metering_1","Sub_metering_2","Sub_metering_3"),
       
       lty = c(1,1,1), col = c("black","red","blue"))

 dev.off()


PLOT 4
df <- read.table("C:/Users/faheera/Desktop/Coursera/course_3/peer_graded/household_power_consumption_1.txt", header = TRUE, sep = ";")

df <- df[complete.cases(df),]


datetime <- as.POSIXct(paste(df$Date, df$Time), format = "%d/%m/%Y %H:%M:%S")


df <- df[,!(names(df) %in% c("Date","Time"))]
df <- cbind(datetime,df)
df
png("plot4.png", width = 480, height = 480)
par(mfrow=c(2,2))
plot(df$datetime,df$Global_active_power,type = "l",xlab = " ",ylab = "Global Active Power")

plot(df$datetime,df$Voltage,type = "l",xlab = "datetime",ylab = "Voltage")

plot(df$datetime,df$Sub_metering_1,col = "black",type = "l", xlab = " ", ylab = "Energy sub metering")

lines(df$datetime,df$Sub_metering_2, col = "red")

lines(df$datetime, df$Sub_metering_3, col = "blue")

legend("topright",
       
       legend = c("Sub_metering_1","Sub_metering_2","Sub_metering_3"),
       
       lty = c(1,1,1), col = c("black","red","blue"))

plot(df$datetime,df$Global_reactive_power,type = "l",xlab = "datetime",ylab = "Global_reactive_power")

dev.off()



