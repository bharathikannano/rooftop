# rooftop

  isCDDRiskAvailableInfo: computed('axwayConfig', {
    get() {
      return this.get('i18n').t("productSummary.isCDDRiskAvailable.info1_" + this.get('axwayConfig.country').toUpperCase(), {
        default: 'productSummary.isCDDRiskAvailable.info2'});
    }
  }),
        
        
        
          init() {
    this._super(...arguments);
    this.set('isCDDRiskAvailableInfo', this.get('i18n').t("productSummary.isCDDRiskAvailable.info1_" + this.get('axwayConfig.country').toUpperCase(), {
      default: 'productSummary.isCDDRiskAvailable.info2'}));
  },
  
  
  
  
    afterSubmit(formDatum){
    const promise = new EmberPromise(resolve => {
      if (formDatum.get('additionalInfo').CRSETB) {
        resolve('CRSETB');  
      } else {
        resolve();
      }
    });
    promise.then(result => {
      if (result && result.length > 0) {
        if(result === 'CRSETB') {
          this.get('rdcModalManager')
          .showDialogModal({
            level: 'error',
            title: this.get('i18n').t('ServiceRequest.COMMON.crsMessage.title'),
            message: this.get('i18n').t('ServiceRequest.COMMON.crsMessage.CRSETB'),
            rejectButtonLabel: this.get('i18n').t('ServiceRequest.COMMON.button.cancel'),
            acceptButtonLabel: this.get('i18n').t('ServiceRequest.COMMON.button.ok')
          })
          .then(() => {
              this.transitionTo('serviceRequest.new-request');
          })
          .catch(() => {});
        }
      }
    });
  },
