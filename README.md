# This code is to split the 3 Gigs Image into 50*50 tiles in selected regions.
clear;
j = 20;
i=0;

% Following are the five images of the same patch taken at different times

name1 = 'citywest_water_2014nov17_air_vis_10cm_mga55_clipped.jp2';
name2 = 'city-west-water_2015oct02_air_vis_10cm_mga55_clipped.jp2';
name3 = 'city-west-water_2016apr25_air_vis_10cm_mga55_clipped.jp2';
name4 = 'city-west-water_2016oct14_air_vis_10cm_mga55_clipped.jp2';
name5 = 'city-west-water_2017jan25_air_vis_10cm_mga55_clipped.jp2';

% Selecting a region of image to be divided into subimages

    [A,clr]=imread(name1,'PixelRegion',{[(j*500)+1,(j+1)*500],[1,100000]});
    
    % Dividing into subimages (50 * 50 meter) where 1 pixel = 10 cm
    % 500*500 pixels = 50*50 meter
    
    row1=0;col1=0;
    while row1<1
        col1=0;
        while col1<200
            % Dividing row-wise
            sub_img = A((row1*500)+1:(row1+1)*500,(col1*500)+1:(col1+1)*500,:);
            col1=col1+1;
            % Saving images in filename sequentially(i.e. 0.jpg,1.jpg,2.jpg,...)
            filename = ['image_2014/Img' num2str(i) '.jpg'];
            imwrite(sub_img,filename);
            i=i+1;
        end
        row1=row1+1;
    end
    
 
