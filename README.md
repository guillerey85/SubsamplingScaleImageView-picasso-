SubsamplingScaleImageView + Picasso



SubsamplingScaleImageView fullscreenImage = findViewById(R.id.fullscreen_image);

String imageUrl = getIntent().getStringExtra("image_url");
        Picasso.get().load(imageUrl).into(new Target() {
                @Override
                public void onBitmapLoaded(Bitmap bitmap, Picasso.LoadedFrom from) {
                    fullscreenImage.setImage(ImageSource.bitmap(bitmap));}
                @Override
                public void onBitmapFailed(Exception e, Drawable errorDrawable) {
                    Toast.makeText(getApplicationContext(), "Error", Toast.LENGTH_LONG).show();}
                @Override
                public void onPrepareLoad(Drawable placeHolderDrawable) {
                // Mostrar un indicador de carga tuyo
                }});
            Picasso.get()
                    .load(imageUrl)
                    .into(new Target() {
                        @Override
                        public void onBitmapLoaded(Bitmap bitmap, Picasso.LoadedFrom from) {
                            fullscreenImage.setMinimumScaleType(SubsamplingScaleImageView.SCALE_TYPE_CENTER_CROP);
                            fullscreenImage.setZoomEnabled(true);
                            fullscreenImage.setPanEnabled(true);}
                        @Override
                        public void onBitmapFailed(Exception e, Drawable errorDrawable) {
                            Toast.makeText(getApplicationContext(), "Error", Toast.LENGTH_LONG).show();                        }
                        @Override
                        public void onPrepareLoad(Drawable placeHolderDrawable) {
                            Toast.makeText(getApplicationContext(), "Cargando", Toast.LENGTH_LONG).show();
                            
                            }});
