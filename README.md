# rooftop

      desc: 'We are unable to open an account for you.',
      maxAttemptReachedMsg: 'Sorry, You have exceeded the maximum number of attempts.',
      info2: 'You can also visit any of our branches where we will be happy to assist you.',
      info1_CI: 'Please contact the Customer Contact Centre on +225 2030 3281.',
      info1_KE: 'Please contact the Customer Contact Centre on +254 203 293900 or +254 703 093900.',
      info1_GH: 'Please contact the Customer Contact Centre on +233 302740100.',
      info1_UG: 'Please contact the Customer Contact Centre on +256 200524100 or +256 313294100.',
      info1_TZ: 'Please contact the Customer Contact Centre on +255 222164999 , +255 784109999 or +255 768986999.',
      info1_BW: 'Please contact the Customer Contact Centre on +267 361 5800.',
      info1_ZM: 'Please contact the Customer Contact Centre on +260 966751500.',
      info1_ZW: 'Please contact the Customer Contact Centre on +263 242 254281 - 3.',
      info1_NG: 'Please contact the Customer Contact Centre on +234 1270 2611 - 4.'
      
      
              <li>
          {{isCDDRiskAvailableInfo}}
        </li>
        
        
        
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
